---
title: "learn-message-java"
date: 2023-04-17
---

学习链接
- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E5%90%8E%E7%AB%AF%E6%8A%80%E6%9C%AF%E9%9D%A2%E8%AF%9538%E8%AE%B2
- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%20%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%2078%20%E8%AE%B2-%E5%AE%8C
- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%20%E6%80%A7%E8%83%BD%E4%BC%98%E5%8C%96%E5%AE%9E%E6%88%98-%E5%AE%8C
- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98
- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E9%9D%A2%E8%AF%95%E7%B2%BE%E8%AE%B2

### JAVA 语言中有8中基本类型
byte, char,short,int,long,float,double,boolean <br>
https://blog.csdn.net/qq_37688023/article/details/85106894

## String 
[String.intern()](https://tech.meituan.com/2014/03/06/in-depth-understanding-string-intern.html)

### 线程状态
Java线程有以下几种状态：

- New（新建）：线程被创建但还没有启动，此时处于New状态。

- Runnable（可运行）：线程被启动后，进入Runnable状态，表示线程正在运行或者等待CPU资源运行。

- Blocked（阻塞）：线程被阻塞，即线程等待某个条件的释放，比如等待I/O操作完成、等待获取一个synchronized锁或者等待某个对象的notify()或notifyAll()方法的调用等。

- Waiting（等待）：线程进入等待状态，等待其他线程的通知或者某些条件的满足，此时该线程不会占用CPU资源，直到其他线程调用该线程的notify()或notifyAll()方法，或者等待的时间到达后线程被唤醒。

- Timed Waiting（计时等待）：线程进入计时等待状态，等待指定时间内的其他线程的通知或者某些条件的满足，此时该线程也不会占用CPU资源，直到等待的时间到达后线程被唤醒。

- Terminated（终止）：线程运行结束后，进入Terminated状态。

[LongAdder解析](https://juejin.cn/post/7103872764984950797)

[volatile 关键字作用](http://www.51gjie.com/java/574.html)


### 线程池
[SynchronousQueue原理解析](https://www.jianshu.com/p/af6f83c78506)

线程池四种拒绝策略
- AbortPolicy、DiscardPolicy、DiscardOldestPolicy、CallerRunsPolicy

6 种常见的线程池
- 即 FixedThreadPool、CachedThreadPool、ScheduledThreadPool、SingleThreadExecutor、SingleThreadScheduledExecutor 和 ForkJoinPool

线程池中比较常用的是 3 种阻塞队列
- 即 LinkedBlockingQueue、SynchronousQueue、DelayedWorkQueue

[ThreadPoolExecutor 线程池 线程异常，会移除异常的，新增一个新的， futureTask 会吞掉异常](https://www.cnblogs.com/fanguangdexiaoyuer/p/12332082.html) submit 不会抛出异常 需要借助 future.get 来捕获异常， execute 会直接抛出异常

[并发编程面试题](https://www.mianshi.online/multi-thread-loop-print.html)

### 知识点
[tomcat是如何打破双亲委派机制的](https://developer.aliyun.com/article/1081332)

分布式 CAP 定理， raft 保证 CP

### 分布式ID
- 数据库生成  （id，  businessType， number），select for update 然后更新  （1、数据库自增   2、按业务逐个获取   3、按业务批量获取）
- zookeeper 的临时有序节点 
- redis 的 incr
- snowflake 雪花算法

[NIO netty](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%20%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E9%9D%A2%E8%AF%95%E7%B2%BE%E8%AE%B2/38%20%20%E5%AF%B9%E6%AF%94Java%E6%A0%87%E5%87%86NIO%E7%B1%BB%E5%BA%93%EF%BC%8C%E4%BD%A0%E7%9F%A5%E9%81%93Netty%E6%98%AF%E5%A6%82%E4%BD%95%E5%AE%9E%E7%8E%B0%E6%9B%B4%E9%AB%98%E6%80%A7%E8%83%BD%E7%9A%84%E5%90%97%EF%BC%9F-%E6%9E%81%E5%AE%A2%E6%97%B6%E9%97%B4.md)

[NIO](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98/11%20%20%E7%AD%94%E7%96%91%E8%AF%BE%E5%A0%82%EF%BC%9A%E6%B7%B1%E5%85%A5%E4%BA%86%E8%A7%A3NIO%E7%9A%84%E4%BC%98%E5%8C%96%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86.md)

[netty 中使用的 select poll  epoll](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98/08%20%20%E7%BD%91%E7%BB%9C%E9%80%9A%E4%BF%A1%E4%BC%98%E5%8C%96%E4%B9%8BIO%E6%A8%A1%E5%9E%8B%EF%BC%9A%E5%A6%82%E4%BD%95%E8%A7%A3%E5%86%B3%E9%AB%98%E5%B9%B6%E5%8F%91%E4%B8%8BIO%E7%93%B6%E9%A2%88%EF%BC%9F.md)


[java中的序列化](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98/09%20%20%E7%BD%91%E7%BB%9C%E9%80%9A%E4%BF%A1%E4%BC%98%E5%8C%96%E4%B9%8B%E5%BA%8F%E5%88%97%E5%8C%96%EF%BC%9A%E9%81%BF%E5%85%8D%E4%BD%BF%E7%94%A8Java%E5%BA%8F%E5%88%97%E5%8C%96.md)


### java 序列化 和 单例
一个序列化了的单例
```
import java.io.Serializable;

public class Singleton implements Serializable {
    private static final long serialVersionUID = 1L;
    
    private static Singleton instance;

    private Singleton() {
        // 私有构造方法
    }

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }

    protected Object readResolve() {
        return getInstance();
    }
}

```

### tcp中的四次挥手
在 TCP 四次挥手中，TIME_WAIT 状态出现在主动关闭方。具体的四次挥手流程如下：

1. 第一步，主动关闭方发送一个 FIN（FIN=1）报文给被动关闭方，表示主动关闭方不再发送数据。主动关闭方进入 FIN_WAIT_1 状态。

2. 第二步，被动关闭方接收到 FIN 报文后，发送一个 ACK（ACK=1）报文作为确认，表示被动关闭方已经收到了主动关闭方的关闭请求。被动关闭方进入 CLOSE_WAIT 状态。

3. 第三步，被动关闭方发送一个 FIN 报文给主动关闭方，表示被动关闭方也希望关闭连接。被动关闭方进入 LAST_ACK 状态。

4. 第四步，主动关闭方接收到 FIN 报文后，发送一个 ACK 报文作为确认，并进入 TIME_WAIT 状态。主动关闭方等待一段时间（通常是两倍的 MSL，即最长报文段生存时间），以确保被动关闭方接收到了 ACK 报文并丢弃了可能延迟到达的数据。

在 TIME_WAIT 状态期间，主动关闭方会等待一段时间，以确保旧连接上的所有报文都被丢弃，避免与新的连接混淆。在等待时间结束后，主动关闭方将结束 TIME_WAIT 状态，完全关闭连接。

总结而言，在 TCP 四次挥手中，TIME_WAIT 状态出现在主动关闭方，用于确保连接的可靠关闭。

### 线程间通信

https://www.finclip.com/news/f/37014.html

共享内存和消息传递


### 进程间通信
https://worktile.com/kb/ask/7774.html

管道（Pipe）：管道是一种半双工的通信方式，可以用于父子进程或兄弟进程之间的通信。在Linux系统中，通过pipe()系统调用可以创建一个匿名管道，其中一个进程将数据写入管道，而另一个进程从管道中读取数据。

命名管道（Named Pipe）：命名管道也是一种管道，但不仅限于父子进程或兄弟进程之间的通信。命名管道使用一个特殊文件作为通信介质，多个进程可以通过打开这个文件来进行通信。

共享内存（Shared Memory）：多个进程可以通过访问共享内存区域来进行数据交换和共享。进程可以在共享内存中读取和写入数据，但需要通过同步机制（如互斥锁、信号量等）来保证对共享内存的并发访问的正确性。

消息队列（Message Queue）：消息队列是一种先进先出（FIFO）的数据结构，多个进程可以通过消息队列进行异步通信。一个进程将消息放入队列，而另一个进程从队列中取出消息进行处理。

信号量（Semaphore）：信号量是一种用于控制并发访问资源的同步机制。进程可以对信号量进行等待（阻塞）或者释放（唤醒）操作，通过改变信号量的值来实现进程之间的同步与互斥。

### 单例
除了静态初始化和加锁双重判定，还可以可使用内部类的方式
```
// 懒汉模式 内部类实现
public final class Singleton {
	public List<String> list = null;// list 属性
 
	private Singleton() {// 构造函数
		list = new ArrayList<String>();
	}
 
	// 内部类实现
	public static class InnerSingleton {
		private static Singleton instance=new Singleton();// 自行创建实例
	}
 
	public static Singleton getInstance() {
		return InnerSingleton.instance;// 返回内部类中的静态变量
	}
}
```



套接字（Socket）：套接字是一种网络通信的方式，可以在同一台机器上的不同进程之间进行通信，也可以在网络中的不同主机之间进行通信。套接字提供了一种灵活的、可靠的通信机制。


### 事务的传播级别
事务的传播行为是指在多个事务之间进行操作时，事务如何进行传播和相互影响的方式。在Java中，可以使用@Transactional注解来指定事务的传播行为，并通过Propagation属性来设置传播级别。

以下是常见的传播级别：

REQUIRED（默认级别）：如果当前存在事务，则加入该事务；如果没有事务，则创建一个新事务。这是最常用的级别。

SUPPORTS：如果当前存在事务，则加入该事务；如果没有事务，则以非事务方式执行。

MANDATORY：要求当前存在事务，如果没有事务则抛出异常。

REQUIRES_NEW：创建一个新事务，并挂起当前事务（如果存在）。

NOT_SUPPORTED：以非事务方式执行操作，如果当前存在事务，则将其挂起。

NEVER：以非事务方式执行操作，如果当前存在事务，则抛出异常。

NESTED：如果当前存在事务，则创建一个嵌套事务并在其中执行操作。如果没有事务，则创建一个新事务。

这些级别可以根据具体的业务需求进行选择。传播级别可以确保在多个事务之间正确处理事务的边界和隔离性。

### String 的不可变好处
- 使用字符串常量池
- 适合作为 HashMap 的 key
- 缓存 HashCode
- 线程安全

### AQS 源码
https://javadoop.com/post/AbstractQueuedSynchronizer

### NEW 一个对象步骤
https://blog.csdn.net/qq_44309181/article/details/111579069 <br>

### ReentrantLock 
[实现原理](https://juejin.cn/post/6844903805683761165) <br>
[源码解析](https://tech.meituan.com/2019/12/05/aqs-theory-and-apply.html) <br>

双向链表中，第一个节点为虚节点，其实并不存储任何信息，只是占位。真正的第一个有数据的节点，是在第二个节点开始的<br>
存在两个队列 1、CLH双向链表  2、 condition.await() and condition.single() 的 单向链表<br>
SharedNode 和 ExclusiveNode

reentrantlock 等待队列为啥使用空的head节点 <br>
1. 简化逻辑
2. 减少条件判断
3. 提高性能
4. 便于实现 FIFO

LockSuport.park  vs  ForkJoinPool.managedBlock， JDK 17 开始在 AQS 中混合使用它们，是为了 兼容未来的虚拟线程与轻量线程调度机制

### CountDownLatch
CountDownLatch.await() 使用的是共享Node

### threadLocal
[使用弱引用](https://blog.csdn.net/qq_44391293/article/details/141429344)

### 实现线程同步的方式
1. ReentrantLock condition的 await signl 方式
1. Synchronized  new Object().wait notify 方式
1. AtomicInteger 的cas方式
2. Thread.join方式
3. CyclickBarrier
4. CountDownLatch
5. Semaphere 信号量的机制
6. Thread sleep 的方式

### 精度丢失
BigDecimal： https://blog.csdn.net/wangxufa/article/details/121722126 <br>
计算机如何保存小数：http://kaito-kidd.com/2018/08/08/computer-system-float-point/ <br>

### 对象引用
https://cloud.tencent.com/developer/article/1953573

### 线程安全
ConcurrentHashMap 的 get 没有加锁， 核心的 node 数组等使用 volatile 修饰   https://blog.csdn.net/Saintmm/article/details/121281918   <br>


### 一些链接
https://javabetter.cn/home.html  <br>

