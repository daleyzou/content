其他基础知识

#### tcp 需要三次握手
- 由发送端判断，避免重复的、过期的、错误的连接建立
- 交换双方的初始序列号 （重复的、无序的、丢失）


#### tcp 的四次挥手


#### tcp 相关连接状态
TIME_WAIT 、CLOSE_WAIT 
```
netstat  -anp | grep TIME_WAIT | wc -l


```
