---
title: "Learn Message Redis"
date: 2023-04-17T21:13:11+08:00
draft: false
---

#### redis 数据结构
Redis 数据库提供了丰富的键值对类型，其中包括了 String、List、Hash、Set 和 Sorted Set 这五种基本键值类型。此外，Redis 还支持位图、HyperLogLog、Geo 等扩展数据类型。<br>
省内存的数据结构<br>
简单动态字符串（SDS）、压缩列表（ziplist）和整数集合（intset） <br>
嵌入式字符串<br>
一个是使用连续的内存空间，避免内存碎片开销；二个是针对不同长度的数据，采用不同大小的元数据

ziplist 的最大特点，就是它被设计成一种内存紧凑型的数据结构，占用一块连续的内存空间<br>
一个 quicklist 就是一个链表，而链表中的每个元素又是一个 ziplist<br>
listpack 中每个列表项不再包含前一项的长度了，因此当某个列表项中的数据发生变化，导致列表项长度变化时，其他列表项的长度是不会受影响的，因而这就避免了 ziplist 面临的连锁更新问题。<br>
 Radix Tree 的最大特点是适合保存具有相同前缀的数据，从而实现节省内存空间的目标，以及支持范围查询<br>

 Redis server 启动后，它的主要工作包括接收客户端请求、解析请求和进行数据读写等操作，是由单线程来执行的<br>
 Redis 还启动了 3 个线程来执行文件关闭、AOF 同步写和惰性删除等操作<br>
 Redis 6.0 中新设计实现的多 IO 线程机制。这个机制的设计主要是为了使用多个 IO 线程，来并发处理客户端读取数据、解析命令和写回数据<br>
 
 
```
typedef struct redisObject {
    unsigned type:4; //redisObject的数据类型，4个bits
    unsigned encoding:4; //redisObject的编码类型，4个bits
    unsigned lru:LRU_BITS;  //redisObject的LRU时间，LRU_BITS为24个bits
    int refcount; //redisObject的引用计数，4个字节
    void *ptr; //指向值的指针，8个字节
} robj;
```

#### redis 字符串实现
char * 存在两个问题 1、不能迅速获取字符数组长度  2、字符串间拼接复杂且效率低

##### SDS数据结构
- len 字符数组现有长度
- alloc 字符数组的分配空间长度
- flags SDS类型
- buf[] 字符数组

因为 SDS 结构中记录了字符数组已占用的空间和被分配的空间，这就比传统 C 语言实现的字符串能带来更高的操作效率
- char flags 表示不同的结构体类型， sdshdr8、sdshdr16、sdshdr32 和 sdshdr64
- 采用紧凑的方式分配内存
#### redis list 实现

#### redis hash 实现
- 针对哈希冲突，Redis 采用了链式哈希
- 渐进式 rehash 设计
- rehash 的扩容大小是当前 ht[0]已使用大小的 2 倍
- 给dictRehash传入的循环次数参数为1，表明每迁移完一个bucket ，就执行正常操作

##### 扩容条件
1. 条件一：ht[0]的大小为 0。
2. 条件二：ht[0]承载的元素个数已经超过了 ht[0]的大小，同时 Hash 表可以进行扩容。 (根据 RDB 和 AOF 的执行情况)
3. 条件三：ht[0]承载的元素个数，是 ht[0]的大小的 dict_force_resize_ratio 倍，其中，dict_force_resize_ratio 的默认值是 5。


#### redis set 实现

#### redis sorted set 实现
组合使用跳表和哈希表<br>
跳表是一个多层的有序链表<br>
跳表设计采用随机的方法来确定每个结点的层数<br>

#### 淘汰策略
近似 LRU 算法、LFU 算法、按 TTL 值淘汰、随机淘汰、不淘汰<br>
支持开启惰性删除， 数据大于 64 条或者数据量大时，可以由后台线程取做内存空间的释放

#### redis 淘汰策略-LRU
redisObject 结构体中的 lru 变量 <br>
随机选取key加入数组 ，配置项 maxmemory-samples 决定的，该配置项的默认值是 5 <br>
待淘汰的候选键值对集合, EvictionPoolLRU 数组分配内存空间，该数组的大小由宏定义 EVPOOL_SIZE（在 evict.c 文件中）决定，默认是 16 个元素 <br>


#### redis 淘汰策略-LFU
1. 第一部分是 lru 变量的高 16 位，是以 1 分钟为精度的 UNIX 时间戳
2. 第二部分是 lru 变量的低 8 位，被设置为宏定义 LFU_INIT_VAL（在server.h文件中），默认值为 5
3. 把这个时长除以 lfu_decay_time 的值，并把结果作为访问次数的衰减大小(在默认情况下，访问次数的衰减大小就是等于上一次访问距离当前的分钟数)
4. 根据当前访问更新访问次数 (取倒数，当前访问次数越大，增加概率越小)
```
uint8_t LFULogIncr(uint8_t counter) {
    if (counter == 255) return 255; //访问次数已经等于255，直接返回255
    double r = (double)rand()/RAND_MAX;  //计算一个随机数
    double baseval = counter - LFU_INIT_VAL;  //计算当前访问次数和初始值的差值
    if (baseval < 0) baseval = 0; //差值小于0，则将其设为0
    double p = 1.0/(baseval*server.lfu_log_factor+1); //根据baseval和lfu_log_factor计算阈值p
    if (r < p) counter++; //概率值小于阈值时,
    return counter;
}
```
LFU 算法相比其他算法来说，更容易把低频访问的冷数据尽早淘汰掉，这也是它的适用场景<br>
访问次数按时间衰减和访问次数按概率增加<br>
基于异步删除的数据淘汰过程，实际上会根据要删除的键值对包含的元素个数，来决定是实际使用后台线程还是主线程来进行删除操作<br>
删除操作实际上是包括了两步子操作。
1. 子操作一：将被淘汰的键值对从哈希表中去除，这里的哈希表既可能是设置了过期 key 的哈希表，也可能是全局哈希表。
2. 子操作二：释放被淘汰键值对所占用的内存空间。


#### 一条 redis 指令的执行过程
1. 操作系统io多路复用， epoll 一次获取多个就绪描述符
2. 命令读取
3. 命令解析
4. 命令执行
5. 结果返回

#### AOP 重写
 AOF 重写的四个触发时机
1. 时机一：bgrewriteaof 命令被执行。
2. 时机二：主从复制完成 RDB 文件解析和加载（无论是否成功）。
3. 时机三：AOF 重写被设置为待调度执行。
4. 时机四：AOF 被启用，同时 AOF 文件的大小比例超出阈值，以及 AOF 文件的大小绝对值超出阈值。

#### 主从复制
全量复制、增量复制和长连接同步<br>
基于状态机的设计思想<br>
整个复制过程分成四个阶段，分别是初始化、建立连接、主从握手、复制类型判断与执行<br>

#### 哨兵
一旦哨兵判断主节点客观下线了，那么哨兵就会进行哨兵 Leader 选举 <br>
要比较哨兵的纪元，以及 master 记录的 Leader 纪元，这样才能满足 Raft 协议对 Follower 在一轮投票中只能投一票的要求 <br>
哨兵会使用 sentinelRedisInstance 结构体来记录主节点的信息，在这个结构体中又记录了监听同一主节点的其他哨兵的信息<br>
获得其他哨兵的信息,发布订阅（Pub/Sub）通信方法

#### redis cluster
Gossip 协议通信、集群关键命令和数据迁移等机制<br>
对于 Redis 来说，集群节点信息包括了节点名称、IP、端口号等，而节点运行状态主要用两个时间来表示，分别是节点向其他节点发送 PING 消息的时间，以及它自己收到其他节点返回的 PONG 消息的时间。最后，集群中数据的分布情况，在 Redis 中就对应了 Redis Cluster 的 slots 分配情况，也就是每个节点拥有哪些 slots。<br>

当集群节点按照 Gossip 协议工作时，每个节点会以一定的频率从集群中随机挑选一些其他节点，把自身的信息和已知的其他节点信息，用 PING 消息发送给选出的节点。而其他节点收到 PING 消息后，也会把自己的信息和已知的其他节点信息，用 PONG 消息返回给发送节点<br>

```
#define CLUSTERMSG_TYPE_PING 0  //Ping消息，用来向其他节点发送当前节点信息
#define CLUSTERMSG_TYPE_PONG 1  //Pong消息，对Ping消息的回复
#define CLUSTERMSG_TYPE_MEET 2  //Meet消息，表示某个节点要加入集群
#define CLUSTERMSG_TYPE_FAIL 3  //Fail消息，表示某个节点有故障
```
要通过 Ping-Pong 消息发送节点自身的信息，以及节点已知的其他节点的信息<br>
随机选择节点发送， clusterCron 函数先通过随机选择五个节点，然后，再在其中挑选和当前节点最长时间没有发送 Pong 消息的节点，作为目标节点

```
```
