---
title: "My Normal Link"
date: 2020-12-01T08:38:41+08:00
---

[Java Collection 移除元素的几种方式](https://juejin.cn/post/6844904035766501384)

'''  

for (int i = 0; i < aList.size(); i++) {
if ("abc".equals(aList.get(i))) {
aList.remove(i--);// 索引回溯
}  

'''

[i++不是原子运算](https://www.jianshu.com/p/a47b141452ce)  [为什么不是原子操作](https://blog.csdn.net/qq_35425070/article/details/83866209)

    内存屏障是个CPU指令,Java内存模型中volatile变量就是通过在写操作之后会插入一个store屏障，在读操作之前会插入一个load屏障，来实现的“禁止指令重排序”


#### java线程池
1、[java线程池](https://tech.meituan.com/2020/04/02/java-pooling-pratice-in-meituan.html)

2、[Java中的ThreadPoolExecutor线程池](https://www.jianshu.com/p/ffda79c38f31)

[rpc框架](https://www.jianshu.com/p/28e48e5f9c73)

[@Autowired底层实现](https://juejin.cn/post/6844903957135884295)

[和为定值k的子数组长度](https://blog.csdn.net/study_000/article/details/77524798)

### MySQL

[mysql与redis数据同步](https://www.cnblogs.com/gered/p/11737388.html)

[mvcc机制](https://blog.csdn.net/qq_35190492/article/details/109044141)

[为什么 MySQL 使用 B+ 树](https://draveness.me/whys-the-design-mysql-b-plus-tree/)

[myisam vs innodb区别](https://www.runoob.com/w3cnote/mysql-different-nnodb-myisam.html)

[一颗高度为3的B+树到底能存多少数据呢](https://juejin.cn/post/6973647815473889311)

[myslq B+树和其他数据结构的比较](https://www.cnblogs.com/aspirant/p/9214485.html)

[mysql 一页 16 KB](https://blog.csdn.net/LJFPHP/article/details/105318995)

[redo log vs undo log 区别](https://learnku.com/articles/49614)

[mysql redo log](https://www.cnblogs.com/ZhuChangwu/p/14096575.html)

[mysql 索引类型](https://segmentfault.com/a/1190000037683781#:~:text=%E6%8C%89%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E5%88%86%E7%B1%BB%E5%8F%AF,%E5%A4%8D%E5%90%88%E7%B4%A2%E5%BC%95%E3%80%81%E7%BB%84%E5%90%88%E7%B4%A2%E5%BC%95%EF%BC%89%E3%80%82)

[mysql 全文索引](https://zhuanlan.zhihu.com/p/35675553)

[mysql mvcc机制](https://zhuanlan.zhihu.com/p/52977862)

[mysql char varchar]()

### IO

[异步io、NIO、AIO](https://blog.csdn.net/weixin_43122090/article/details/105462088)

### 垃圾处理

[G1垃圾收集器](https://tech.meituan.com/2016/09/23/g1.html)

### Java知识点
[transmittable-thread-local](https://github.com/alibaba/transmittable-thread-local/issues/123)

[CAS 原子操作](https://juejin.cn/post/6844904177856937991)
    cmpxchg指令，lock前缀指令执行时，要么锁住 “总线锁”，要么锁住 “缓存锁”，目的都是为了保证 “比较、交换” 这个复合操作的原子性


[volatile原理](https://zhuanlan.zhihu.com/p/77085695)

[JVM内存模型](https://www.cnblogs.com/chenyangyao/p/5269622.html)

[java8 ArrayList](https://zhuanlan.zhihu.com/p/34443888)

[虚拟机垃圾回收](https://www.infoq.cn/article/zoyqri4c-bfkmubmzmkn)

[对B+树，B树，红黑树的理解](https://www.jianshu.com/p/86a1fd2d7406)

[浅谈AVL树,红黑树,B树,B+树原理及应用](https://blog.csdn.net/whoamiyang/article/details/51926985)

[B+树详解](https://ivanzz1001.github.io/records/post/data-structure/2018/06/16/ds-bplustree)

[Synchronize和ReentrantLock区别](https://juejin.cn/post/6844903695298068487)

[深入理解ReentrantLock的实现原理](https://juejin.cn/post/6844903805683761165)

[从ReentrantLock的实现看AQS的原理及应用](https://tech.meituan.com/2019/12/05/aqs-theory-and-apply.html)


[线程里该如何返回值 callable runnable]()

[ThreadLocal volatile 线程的内存模型]()

# Redis
[Redis 跳跃表]()

[Redis 字符串实现](https://redisbook.readthedocs.io/en/latest/internal-datastruct/sds.html)

[Java实现跳表](https://leetcode-cn.com/problems/design-skiplist/solution/javashou-xie-shi-xian-tiao-biao-by-feng-omdm0/)

[redis 用skipList , 不用 红黑树](https://juejin.cn/post/6844903446475177998)

[redis 命令的执行过程]()

[redis sds](https://redisbook.readthedocs.io/en/latest/internal-datastruct/sds.html)

[redis通信协议](https://zhuanlan.zhihu.com/p/345327284)

[近似于LRU的内存淘汰策略](https://my.oschina.net/lscherish/blog/4467394)

[redis cluster gossip](https://segmentfault.com/a/1190000038373546)

### 线程池

[线程池](https://tech.meituan.com/2020/04/02/java-pooling-pratice-in-meituan.html)

### Spring框架
[@ASync](https://juejin.cn/post/6858854987280809997)


### Linux
[IO 多路复用](https://juejin.cn/post/6882984260672847879)   

[epoll](https://www.jianshu.com/p/dfd940e7fca2)

[select epoll](https://segmentfault.com/a/1190000003063859)

[零拷贝(Zero-copy) 浅析及其应用 ](https://www.cnblogs.com/rickiyang/p/13265043.html)

### 网络通讯
[为何TCP要三次握手，两次行不行](https://draveness.me/whys-the-design-tcp-three-way-handshake/)

[TCP连接的TIME_WAIT和CLOSE_WAIT 状态解说](https://www.cnblogs.com/kevingrace/p/9988354.html)

[http https](https://www.runoob.com/w3cnote/http-vs-https.html)

[三次握手，四次挥手](https://www.eet-china.com/mp/a44399.html#:~:text=Acknowledgement%20Number%20%E7%A1%AE%E8%AE%A4%E5%BA%8F%E5%88%97%E5%8F%B7,%E6%93%8D%E6%8E%A7TCP%20%E7%8A%B6%E6%80%81%E6%9C%BA%E7%9A%84%E3%80%82)

### 系统
[生成分布式ID的方法]()

### 基础及算法
[avl 红黑树](https://blog.csdn.net/wanderlustLee/article/details/81297253)

### 消息队列
[kafka知识点](https://www.cnblogs.com/crazymakercircle/p/14367425.html)

#### 复习java的知识点链接
https://crossoverjie.top/JCSprout/#/soft-skills/Interview-experience

https://github.com/caison/java-knowledge-mind-map

https://doocs.github.io/jvm/#/

https://github.com/0voice/interview_internal_reference

https://github.com/doocs/advanced-java

https://snailclimb.gitee.io/javaguide/#/?id=java

https://cyc2018.github.io/CS-Notes/#/README

https://github.com/AobingJava/JavaFamily

https://github.com/Jstarfish/JavaKeeper



### 三年了，学习吧
http://www.cyc2018.xyz/

https://javaguide.cn/

https://github.com/0voice/interview_internal_reference

https://osjobs.net/topk/%E5%AD%97%E8%8A%82%E8%B7%B3%E5%8A%A8/

