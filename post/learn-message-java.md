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

[netty 中使用的 select poll  epoll](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98/08%20%20%E7%BD%91%E7%BB%9C%E9%80%9A%E4%BF%A1%E4%BC%98%E5%8C%96%E4%B9%8BIO%E6%A8%A1%E5%9E%8B%EF%BC%9A%E5%A6%82%E4%BD%95%E8%A7%A3%E5%86%B3%E9%AB%98%E5%B9%B6%E5%8F%91%E4%B8%8BIO%E7%93%B6%E9%A2%88%EF%BC%9F.md)

[java中的序列化](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%E5%B9%B6%E5%8F%91%E7%BC%96%E7%A8%8B%E5%AE%9E%E6%88%98/09%20%20%E7%BD%91%E7%BB%9C%E9%80%9A%E4%BF%A1%E4%BC%98%E5%8C%96%E4%B9%8B%E5%BA%8F%E5%88%97%E5%8C%96%EF%BC%9A%E9%81%BF%E5%85%8D%E4%BD%BF%E7%94%A8Java%E5%BA%8F%E5%88%97%E5%8C%96.md)
