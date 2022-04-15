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


#### java 框架
1、[java线程池](https://tech.meituan.com/2020/04/02/java-pooling-pratice-in-meituan.html)

2、[Java中的ThreadPoolExecutor线程池](https://www.jianshu.com/p/ffda79c38f31)

[rpc框架](https://www.jianshu.com/p/28e48e5f9c73)

[@Autowired底层实现](https://juejin.cn/post/6844903957135884295)

[和为定值k的子数组长度](https://blog.csdn.net/study_000/article/details/77524798)

[Mybatis ResultMap和ResultType的差别](https://cloud.tencent.com/developer/article/1455849)

[@Autowired和@Resource的区别](https://juejin.cn/post/7022507865701089317)

[dubbo调用过程](https://dubbo.apache.org/zh/docsv2.7/dev/source/service-invoking-process/)

[dubbo spi 机制](https://dubbo.apache.org/zh/docsv2.7/dev/source/dubbo-spi/)

[Netty 知识点](https://zhuanlan.zhihu.com/p/148726453)

[分布式数据一致性](https://zhuanlan.zhihu.com/p/193802636) 

[线上cpu 100%排查](https://www.cnblogs.com/dennyzhangdd/p/11585971.html)

[dubbo 和 reator](https://www.programminghunter.com/article/5494114964/)

[netty 常见面试题](https://bbs.huaweicloud.com/blogs/273799)

[reactor三种模式对比](https://zhuanlan.zhihu.com/p/69341619)

[dubbo PRC 通信协议](https://dubbo.apache.org/zh/docs/concepts/rpc-protocol/)

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

[mysql 死锁检测](https://bbs.huaweicloud.com/forum/thread-83643-1-1.html)

[mysql char varchar]()

[mysql 不可重复读 和 幻读](https://cloud.tencent.com/developer/article/1450773)

[mysql mvcc的机制](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2/08%20%20%E4%BA%8B%E5%8A%A1%E5%88%B0%E5%BA%95%E6%98%AF%E9%9A%94%E7%A6%BB%E7%9A%84%E8%BF%98%E6%98%AF%E4%B8%8D%E9%9A%94%E7%A6%BB%E7%9A%84%EF%BC%9F.md)

[mysql redo log and binlog](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2/02%20%20%E6%97%A5%E5%BF%97%E7%B3%BB%E7%BB%9F%EF%BC%9A%E4%B8%80%E6%9D%A1SQL%E6%9B%B4%E6%96%B0%E8%AF%AD%E5%8F%A5%E6%98%AF%E5%A6%82%E4%BD%95%E6%89%A7%E8%A1%8C%E7%9A%84%EF%BC%9F.md)

[mysql explain数据行数预估](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2/10%20%20MySQL%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E6%97%B6%E5%80%99%E4%BC%9A%E9%80%89%E9%94%99%E7%B4%A2%E5%BC%95%EF%BC%9F.md)   https://blog.csdn.net/tracymm19891990/article/details/104798190

[mysql order by 流程]()

[select 执行流程](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/MySQL%E5%AE%9E%E6%88%9845%E8%AE%B2/01%20%20%E5%9F%BA%E7%A1%80%E6%9E%B6%E6%9E%84%EF%BC%9A%E4%B8%80%E6%9D%A1SQL%E6%9F%A5%E8%AF%A2%E8%AF%AD%E5%8F%A5%E6%98%AF%E5%A6%82%E4%BD%95%E6%89%A7%E8%A1%8C%E7%9A%84%EF%BC%9F.md)

[mysql 刷盘机制](https://blog.csdn.net/qq_40687433/article/details/112540401)

[半一致性读 和 当前读](https://www.linuxidc.com/Linux/2017-02/140843.htm)

### IO

[异步io、NIO、AIO](https://blog.csdn.net/weixin_43122090/article/details/105462088)

### 垃圾处理

[G1垃圾收集器](https://tech.meituan.com/2016/09/23/g1.html)

[cms and g1](https://cloud.tencent.com/developer/article/1647637)

[虚拟机参数设置](https://cloud.tencent.com/developer/article/1695047)

[Gc roots 有哪些](https://juejin.cn/post/6844904163927654408)

[虚拟机内存划分](https://juejin.cn/post/6935417287990050846)

[full gc 问题排查](https://blog.csdn.net/weixin_39626180/article/details/113073213)

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

[threadlocal 内存泄露](https://zhuanlan.zhihu.com/p/56214714)

[Java8 hashmap](https://zhuanlan.zhihu.com/p/72296421) 详细扩容流程

[线程里该如何返回值 callable runnable]()

[ThreadLocal ](https://www.cnblogs.com/wupeixuan/p/12638203.html)

[LongAdder vs AutomicInteger]()

[ArrayBlockingQueue 的底层实现](https://www.cnblogs.com/tuyang1129/p/12683373.html)

[LinkedBlockingQueue源码分析](https://mp.weixin.qq.com/s/MiS4QXPLIQb67zfLfW4RAw)

[双亲委派](https://www.cnblogs.com/hollischuang/p/14260801.html)

[三个线程循环打印 A B C](https://segmentfault.com/a/1190000021433079)

[线程池线程异常](https://zhuanlan.zhihu.com/p/136571068)

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

[基于Redis的分布式锁和Redlock算法](https://blog.51cto.com/u_15064632/2601502)

[dictGetRendomKeys 实现获取字典随机key进行删除](https://segmentfault.com/a/1190000020547849)

[redis lru and lfu实现](https://cherish-ls.github.io/2020/08/04/LRU%E5%92%8CLFU%E7%AE%97%E6%B3%95%E4%BB%A5%E5%8F%8A%E5%85%B6%E5%9C%A8Redis%E4%B8%AD%E7%9A%84%E5%AE%9E%E7%8E%B0/)

[redis 批处理 、lua脚本](https://juejin.cn/post/6926414112788316174)

### 线程池

[线程池](https://tech.meituan.com/2020/04/02/java-pooling-pratice-in-meituan.html)

### Spring框架
[@ASync](https://juejin.cn/post/6858854987280809997)

[spring用到哪些设计模式](https://blog.51cto.com/u_15072908/3380487)


### Linux
[IO 多路复用](https://juejin.cn/post/6882984260672847879)   

[epoll](https://www.jianshu.com/p/dfd940e7fca2)

[select epoll](https://segmentfault.com/a/1190000003063859)

[零拷贝(Zero-copy) 浅析及其应用 ](https://www.cnblogs.com/rickiyang/p/13265043.html)

[cpu三级缓存 mesi机制](https://zhuanlan.zhihu.com/p/411904385)

[mmap sendFile  splice 的区别](https://www.guodong.plus/2020/0802-153558/)

### 网络通讯
[为何TCP要三次握手，两次行不行](https://draveness.me/whys-the-design-tcp-three-way-handshake/)

[TCP连接的TIME_WAIT和CLOSE_WAIT 状态解说](https://www.cnblogs.com/kevingrace/p/9988354.html)

[http https](https://www.runoob.com/w3cnote/http-vs-https.html)

[三次握手，四次挥手](https://www.eet-china.com/mp/a44399.html#:~:text=Acknowledgement%20Number%20%E7%A1%AE%E8%AE%A4%E5%BA%8F%E5%88%97%E5%8F%B7,%E6%93%8D%E6%8E%A7TCP%20%E7%8A%B6%E6%80%81%E6%9C%BA%E7%9A%84%E3%80%82)

[http2 io多路复用](https://segmentfault.com/a/1190000016975064)

[ip路由原理](https://zhuanlan.zhihu.com/p/338894712)

[浏览器输入URL发生了什么](https://blog.csdn.net/ejennahuang/article/details/114821971)

[计算机IP和子网掩码](https://zhuanlan.zhihu.com/p/50091071)


### 系统
[生成分布式ID的方法](https://blog.nowcoder.net/n/69fd7ba74a2641299d7c484ef454d9d0)

[分库分表的设计思路](https://blog.csdn.net/baihualindesu/article/details/89493070)

[常用设计模式]()

[jvm问题排查](https://blog.csdn.net/GitChat/article/details/79019454)

[系统问题排查](https://www.jianshu.com/p/bca5a49db4b7)

### 基础及算法
[avl 红黑树](https://blog.csdn.net/wanderlustLee/article/details/81297253)

### 消息队列
[kafka知识点](https://www.cnblogs.com/crazymakercircle/p/14367425.html)

[zookeeper如何保证数据一致性](https://www.cnblogs.com/zz-ksw/p/12786067.html#:~:text=%E6%95%B4%E4%B8%AAZooKeeper%20%E9%9B%86%E7%BE%A4%E7%9A%84%E4%B8%80%E8%87%B4,%E9%87%8D%E6%96%B0%E8%BF%9B%E5%85%A5%E6%B6%88%E6%81%AF%E5%B9%BF%E6%92%AD%E9%98%B6%E6%AE%B5%E3%80%82)

[kafka为啥使用消费者组](https://www.pianshen.com/article/27581061419/#:~:text=%E5%A6%82%E6%9E%9C%E5%8F%AA%E6%9C%89%E4%B8%80%E4%B8%AA%E6%B6%88%E8%B4%B9%E8%80%85,%E6%B6%88%E8%B4%B9%E8%80%85%E7%9A%84%E6%95%85%E9%9A%9C%E5%AE%B9%E9%94%99%E3%80%82)

[kafka时间轮算法](https://www.infoq.cn/article/erdajpj5epir65iczxzi)

[kafka ISR](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Kafka%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E4%B8%8E%E5%AE%9E%E6%88%98/27%20%20%E5%85%B3%E4%BA%8E%E9%AB%98%E6%B0%B4%E4%BD%8D%E5%92%8CLeader%20Epoch%E7%9A%84%E8%AE%A8%E8%AE%BA.md)

[kafka消费者组重平衡](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Kafka%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E4%B8%8E%E5%AE%9E%E6%88%98/25%20%20%E6%B6%88%E8%B4%B9%E8%80%85%E7%BB%84%E9%87%8D%E5%B9%B3%E8%A1%A1%E5%85%A8%E6%B5%81%E7%A8%8B%E8%A7%A3%E6%9E%90.md)

[kafka 为啥折磨快](https://www.guodong.plus/2020/0802-153558/)

### 一些题
[真题1](https://blog.csdn.net/Gupaoxueyuan/article/details/104820652)

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

[极客时间资料](https://learn.lianglianglee.com/)

https://www.pdai.tech/md/java/thread/java-thread-x-threadlocal.html 

hh



### 三年了，学习吧
http://www.cyc2018.xyz/

https://javaguide.cn/

https://github.com/0voice/interview_internal_reference

https://osjobs.net/topk/%E5%AD%97%E8%8A%82%E8%B7%B3%E5%8A%A8/

