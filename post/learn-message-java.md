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


