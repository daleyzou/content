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

#### redis 淘汰策略-LRU

#### redis 淘汰策略-LFU

```
```
