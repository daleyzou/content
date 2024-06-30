其他基础知识

#### tcp 需要三次握手
- 由发送端判断，避免重复的、过期的、错误的连接建立
- 交换双方的初始序列号 （重复的、无序的、丢失） SYN ACK SEQ


#### tcp 的四次挥手
- 确认双方都收到关闭 FIN ACK
- 被关闭方继续发送未完成的数据
- 关闭方等待 2MSL 的时间后在完成关闭连接（避免端口被立刻重复使用）

#### tcp 相关连接状态
TIME_WAIT 、CLOSE_WAIT 
```
netstat  -anp | grep TIME_WAIT | wc -l
CLOSE_WAIT： 被动关闭的一方，等待上层应用调度关闭
TIME_WAIT： 主动关闭的一方， 等待 2ML 的时间后关闭

time_wait作用
防止前一个连接上延迟的数据包或者丢失重传的数据包，被后面复用的连接错误的接收
确保连接方能在时间范围内，关闭自己的连接
为了保证客户端发送的最后一个ACK 报文能够到达服务器
```
#### 分布式协议
Raft ，包括 Leader、Follower、Candidate 三种节点类型，哨兵在正常运行时并不像 Raft 协议那样区分了三种节点类型，而是所有哨兵都是对等的。而当哨兵发现主节点故障，要执行故障切换时，会按照 Raft 协议中 Leader 选举的规则，进行投票选出 Leader

#### 链接
https://www.hzhr.cc/wap/c_article-a_show-id_33709.html <br>
https://blog.csdn.net/Weixiaohuai/article/details/120853683

#### 通信方式
- 进程 系统进行资源分配和调度的基本单位
- 线程 是进程的一个实体,是CPU调度和分派的基本单位
##### 进程间通信
管道（有名管道、无名管道）、消息队列、共享内存、信号量、信号、socket
##### 线程间通信
信号量、信号、锁

#### 代理模式和装饰模式的区别
[区别](https://worktile.com/kb/ask/37725.html) <br>

#### tcp 三次握手、四次挥手
https://xiaolincoding.com/network/3_tcp/tcp_interview.html <br>

#### netty 导致的 close_wait 问题
[链接](https://mp.weixin.qq.com/s?__biz=MzU3Njk0MTc3Ng==&mid=2247486020&idx=1&sn=f7cf41aec28e2e10a46228a64b1c0a5c&scene=21#wechat_redirect)
