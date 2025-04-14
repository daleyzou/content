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

Spring 中 Bean 的生命周期大致分为四个阶段：实例化（Instantiation）、属性赋值（Populate）、初始化（Initialization）、销毁（Destruction）

### BeanFactory an ApplicationContext
在 Spring 中，基本容器 BeanFactory 和扩展容器 ApplicationContext 的实例化时机不太一样，BeanFactory 采用的是延迟初始化的方式，也就是说，只有在第一次 getBean() 获取 Bean 的时候，才会实例化 Bean。

而 ApplicationContext 会在启动时预先创建并初始化所有的 Bean，并且包含了 BeanFactory 的所有功能，还增加了国际化支持、事件传播等功能。在 Spring Boot 项目中，一般使用的是 ApplicationContext。 <br>
https://blog.csdn.net/Weixiaohuai/article/details/120853683

### threadLocal
https://javabetter.cn/thread/ThreadLocal.html

### @Autowired and @Resource
https://www.cnblogs.com/think-in-java/p/5474740.html <br>
当两个注解都存在时， 因为 先执行的 CommonAnnotationBeanPostProcessor会完成属性注入，后执行的AutowiredAnnotationBeanPostProcessor， 不会覆盖，[所以 @Resource 会生效](https://www.cnblogs.com/ibigboy/p/16501592.html)

### spring boot  VS  spring cloud  
https://refblogs.com/article/633 <br>

### Akka vs springboot
https://blog.51cto.com/u_16175514/12624615 <br>

### 响应式编程
https://potoyang.gitbook.io/spring-in-action-v5/di-10-zhang-reactor-jie-shao/10.1-li-jie-xiang-ying-shi-bian-cheng

### 底层容器 Tomcat 和 Netty
https://blog.csdn.net/zhangzehai2234/article/details/135175994 <br>


### 附注
spring、dubbo、mybatis、elasticsearch

