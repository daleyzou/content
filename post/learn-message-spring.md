---
title: "Learn Message Spring"
date: 2023-04-17T21:13:42+08:00
draft: true
---

### spring
[相关知识点](https://javabetter.cn/sidebar/sanfene/spring.html) <br>
[spring 三级缓存解决循环依赖](https://cloud.tencent.com/developer/article/1497692)

### 事务的传播机制
https://www.cnblogs.com/vipstone/p/16735893.html <br>
1. Propagation.REQUIRED：默认的事务传播级别，它表示如果当前存在事务，则加入该事务；如果当前没有事务，则创建一个新的事务。
1. Propagation.SUPPORTS：如果当前存在事务，则加入该事务；如果当前没有事务，则以非事务的方式继续运行。
1. Propagation.MANDATORY：（mandatory：强制性）如果当前存在事务，则加入该事务；如果当前没有事务，则抛出异常。
1. Propagation.REQUIRES_NEW：表示创建一个新的事务，如果当前存在事务，则把当前事务挂起。也就是说不管外部方法是否开启事务，1. Propagation.REQUIRES_NEW 修饰的内部方法会新开启自己的事务，且开启的事务相互独立，互不干扰。
1. Propagation.NOT_SUPPORTED：以非事务方式运行，如果当前存在事务，则把当前事务挂起。
1. Propagation.NEVER：以非事务方式运行，如果当前存在事务，则抛出异常。
1. Propagation.NESTED：如果当前存在事务，则创建一个事务作为当前事务的嵌套事务来运行；如果当前没有事务，则该取值等价于 PROPAGATION_REQUIRED。


### 附注
spring、dubbo、mybatis、elasticsearch

