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



