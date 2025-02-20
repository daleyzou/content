其他基础知识

#### tcp 需要三次握手
- 由发送端判断，避免重复的、过期的、错误的连接建立
- 交换双方的初始序列号 （重复的、无序的、丢失） SYN ACK SEQ


#### tcp 的四次挥手
- 确认双方都收到关闭 FIN ACK
- 被关闭方继续发送未完成的数据
- 关闭方等待 2MSL 的时间后在完成关闭连接（避免端口被立刻重复使用）
- 如果被关闭方没有数据要发送，且 TCP 默认开了延迟确认，会变成三次挥手，ack 和 fin 同时发送

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

tcp_tw_reuse 的作用是让客户端快速复用处于 TIME_WAIT 状态的端口，相当于跳过了 TIME_WAIT 状态，这可能会出现这样的两个问题：

历史 RST 报文可能会终止后面相同四元组的连接，因为 PAWS 检查到即使 RST 是过期的，也不会丢弃。
如果第四次挥手的 ACK 报文丢失了，有可能被动关闭连接的一方不能被正常的关闭;
虽然 TIME_WAIT 状态持续的时间是有一点长，显得很不友好，但是它被设计来就是用来避免发生乱七八糟的事情。
```
#### 分布式协议
Raft ，包括 Leader、Follower、Candidate 三种节点类型，哨兵在正常运行时并不像 Raft 协议那样区分了三种节点类型，而是所有哨兵都是对等的。而当哨兵发现主节点故障，要执行故障切换时，会按照 Raft 协议中 Leader 选举的规则，进行投票选出 Leader

Paxos

Raft


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

#### 常用命令
```
ss -lnt // 查看 accept （全连接队列的大小）

# watch -d 'netstat -s | grep overflowed'

ping
mtr
```
  
#### netty 导致的 close_wait 问题
[链接](https://mp.weixin.qq.com/s?__biz=MzU3Njk0MTc3Ng==&mid=2247486020&idx=1&sn=f7cf41aec28e2e10a46228a64b1c0a5c&scene=21#wechat_redirect)

#### tcp 的问题
1. 升级 tcp 的工作很困难
1. tcp 三次握手的时延
2. 存在队头阻塞的问题
3. 网络迁移需要重新建立连接

#### 基于 udp 实现可靠传输
1. 使用 quic 协议
2. 每个 Stream 使用自己的滑动窗口，避免队头阻塞问题
3. 在应用层做控制，基于连接ID做通道复用，而不是tcp四元组 

#### 查看 TCP 连接情况
https://blog.csdn.net/pony12/article/details/115747776 <br> 
```
$ netstat -napt
协议  源ip地址:端口            目的ip地址：端口         状态
tcp  192.168.110.182.64992   117.147.199.51.443     ESTABLISHED
```

#### TCP 特殊情况
在只 bind 没有 listen 时，客户端发送 syn 后会直接收到 rst。 在客户端和自己建立连接、两个客户端同时发起连接时可以在没有listen的情况下成功建立连接 <br>
[同时发送 syn，同时发送 fin](https://blog.csdn.net/m_buddy/article/details/74332423) <br>


#### TCP 抓包工具
tcpdump / wireshark

#### 大数的处理，分而治之的思想
[TOP N 数据的处理](https://blog.nowcoder.net/n/ef169f7ca52549cca91aa50bb1473e7c)
