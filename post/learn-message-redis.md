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

#### redis 淘汰策略-LRU

#### redis 淘汰策略-LFU

#### 一条 redis 指令的执行过程
1. 操作系统io多路复用， epoll 一次获取多个就绪描述符
2. 命令读取
3. 命令解析
4. 命令执行
5. 结果返回
```
```
