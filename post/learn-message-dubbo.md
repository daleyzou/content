学习链接：
https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Dubbo%E6%BA%90%E7%A0%81%E8%A7%A3%E8%AF%BB%E4%B8%8E%E5%AE%9E%E6%88%98-%E5%AE%8C

#### 官方文档
2.7 https://cn.dubbo.apache.org/zh-cn/docsv2.7/dev/source/service-invoking-process/ <br>
3.0 https://cn.dubbo.apache.org/zh-cn/blog/2022/08/01/01-%E4%BB%8E%E4%B8%80%E4%B8%AA%E6%9C%8D%E5%8A%A1%E6%8F%90%E4%BE%9B%E8%80%85%E7%9A%84demo%E8%AF%B4%E8%B5%B7/

#### 服务发现
https://cn.dubbo.apache.org/zh-cn/blog/2021/06/02/dubbo3-%e5%ba%94%e7%94%a8%e7%ba%a7%e6%9c%8d%e5%8a%a1%e5%8f%91%e7%8e%b0/



Dubbo的大致工作流程如下：
1. 服务提供方将自身提供的服务注册到服务注册中心；
1. 服务调用方需要向注册中心预订调用服务的提供方地址列表；
1. 服务注册中心将服务对应的提供方地址列表返回给调用方；
1. 服务调用方根据服务地址信息进行远程服务调用；
1. 服务调用方和服务提供方定时向监控中心发送服务调用次数及调用时间等信息
