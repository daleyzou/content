---
title: "learn-message-jvm"
date: 2023-04-17
---

## java 对象头
在 Java 虚拟机中，每个 Java 对象都有一个对象头（object header），这个由标记字段和类型指针所构成。其中，标记字段用以存储 Java 虚拟机有关该对象的运行数据，如哈希码、GC 信息以及锁信息，而类型指针则指向该对象的类。

在 64 位的 Java 虚拟机中，对象头的标记字段占 64 位，而类型指针又占了 64 位。也就是说，每一个 Java 对象在内存中的额外开销就是 16 个字节。以 Integer 类为例，它仅有一个 int 类型的私有字段，占 4 个字节。因此，每一个 Integer 对象的额外内存开销至少是 400%。这也是为什么 Java 要引入基本类型的原因之一

如果虚拟机开启了压缩指针， 可以把类型指针 从 8 个字节压缩到 4 个字节， 从而对象头总共占用 12 字节

Java 虚拟机会让不同的 @Contended 字段处于独立的缓存行中，因此你会看到大量的空间被浪费掉。

[link](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E6%B7%B1%E5%85%A5%E6%8B%86%E8%A7%A3Java%E8%99%9A%E6%8B%9F%E6%9C%BA/10%20%20Java%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%86%85%E5%AD%98%E5%B8%83%E5%B1%80.md)

## GC
那么什么是 GC Roots 呢？我们可以暂时理解为由堆外指向堆内的引用，一般而言，GC Roots 包括（但不限于）如下几种：

- Java 方法栈桢中的局部变量；
- 已加载类的静态变量；
- JNI handles；
- 已启动且未停止的 Java 线程
- 新生代和老年代之间的引用关系， rememberSet / 卡表中记录“脏”的卡


## jvm 链接
-  https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/JVM%20%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%2032%20%E8%AE%B2%EF%BC%88%E5%AE%8C%EF%BC%89/13%20%E5%B8%B8%E8%A7%81%E7%9A%84%20GC%20%E7%AE%97%E6%B3%95%EF%BC%88GC%20%E7%9A%84%E8%83%8C%E6%99%AF%E4%B8%8E%E5%8E%9F%E7%90%86%EF%BC%89.md

- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BA%20Java%20%E8%99%9A%E6%8B%9F%E6%9C%BA-%E5%AE%8C/06%20%E6%B7%B1%E5%85%A5%E5%89%96%E6%9E%90%EF%BC%9A%E5%9E%83%E5%9C%BE%E5%9B%9E%E6%94%B6%E4%BD%A0%E7%9C%9F%E7%9A%84%E4%BA%86%E8%A7%A3%E5%90%97%EF%BC%9F%EF%BC%88%E4%B8%8A%EF%BC%89.md
- https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E6%B7%B1%E5%85%A5%E6%8B%86%E8%A7%A3Java%E8%99%9A%E6%8B%9F%E6%9C%BA/13%20%20Java%E5%86%85%E5%AD%98%E6%A8%A1%E5%9E%8B.md

[G1垃圾回收器](https://blog.csdn.net/a745233700/article/details/121724998)

[卡表和Rset](https://magicliang.github.io/2018/10/13/%E5%8D%A1%E8%A1%A8%E5%92%8C-RSet/)

## Java中继承类的初始化顺序可以总结为以下几点：

父类静态代码块的初始化。父类的静态代码块在类被加载时执行，且仅执行一次。

子类静态代码块的初始化。子类的静态代码块在类被加载时执行，且仅执行一次。

父类实例变量的初始化。在父类构造函数被调用之前，父类的实例变量被初始化。

父类构造函数的初始化。在父类实例变量被初始化之后，父类的构造函数被调用。

子类实例变量的初始化。在子类构造函数被调用之前，子类的实例变量被初始化。

子类构造函数的初始化。在子类实例变量被初始化之后，子类的构造函数被调用。

需要注意的是，当创建子类对象时，以上顺序逐步执行，以确保父类的初始化顺序在子类之前完成。同时，如果子类没有显示地调用父类构造函数，则默认调用父类的无参构造函数。

## 自己模拟虚拟机溢出场景
https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BA%20Java%20%E8%99%9A%E6%8B%9F%E6%9C%BA-%E5%AE%8C/11%20%E7%AC%AC10%E8%AE%B2%EF%BC%9A%E5%8A%A8%E6%89%8B%E5%AE%9E%E8%B7%B5%EF%BC%9A%E8%87%AA%E5%B7%B1%E6%A8%A1%E6%8B%9F%20JVM%20%E5%86%85%E5%AD%98%E6%BA%A2%E5%87%BA%E5%9C%BA%E6%99%AF.md

jvm 工具
- gceasy 
- MAT
- GCViewer 
- GCViewer 

```
grep -n real gc.log | awk -F"=| " '{ if($8>0.1){ print }}'

jstat -gcutil $pid 1000

iostat -x 1

jstat -gcutil -t 90542 1000 | awk 'BEGIN{pre=0}{if(NR>1) {print $0 "\t" ($12-pre) "\t" $12*100/$1 ; pre=$12 } else { print $0 "\tGCT_INC\tRate"} }' 

ps -p 75 -o rss,vsz
```

查看进程的内存分布情况
```
pmap -x 2154  | sort -n -k3
```

## 垃圾收集器
[Shenandoah 和 ZGC](https://realdaiwei.github.io/2021/06/27/garbage-collector-2/)

[java 17 收集](https://huminxi.netlify.app/2022/07/06/java%208%20vs%20java%2017%20%E5%9E%83%E5%9C%BE%E6%94%B6%E9%9B%86%E5%99%A8/) <br>
[G1 的三色标记法](https://blog.csdn.net/a141210104/article/details/126673800) <br>
[Shenandoah通过读屏障和"Brooks Pointers"解决并发回收](https://blog.csdn.net/weixin_45902285/article/details/121437457) <br>
[ZGC](https://javabetter.cn/jvm/gc-collector.html#zgc) <br>


## 双亲委派机制及其打破情况
[tomcat / spi](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BA%20Java%20%E8%99%9A%E6%8B%9F%E6%9C%BA-%E5%AE%8C/03%20%E5%A4%A7%E5%8E%82%E9%9D%A2%E8%AF%95%E9%A2%98%EF%BC%9A%E4%BB%8E%E8%A6%86%E7%9B%96%20JDK%20%E7%9A%84%E7%B1%BB%E5%BC%80%E5%A7%8B%E6%8E%8C%E6%8F%A1%E7%B1%BB%E7%9A%84%E5%8A%A0%E8%BD%BD%E6%9C%BA%E5%88%B6.md)

[jmm 和 jvm](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/%E6%B7%B1%E5%85%A5%E6%B5%85%E5%87%BA%20Java%20%E8%99%9A%E6%8B%9F%E6%9C%BA-%E5%AE%8C/19%20%E5%A4%A7%E5%8E%82%E9%9D%A2%E8%AF%95%E9%A2%98%EF%BC%9A%E4%B8%8D%E8%A6%81%E6%90%9E%E6%B7%B7%20JMM%20%E4%B8%8E%20JVM.md)

## GC参数说明
[GC链接](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%20%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E9%9D%A2%E8%AF%95%E7%B2%BE%E8%AE%B2/28%20%20%E8%B0%88%E8%B0%88%E4%BD%A0%E7%9A%84GC%E8%B0%83%E4%BC%98%E6%80%9D%E8%B7%AF-%E6%9E%81%E5%AE%A2%E6%97%B6%E9%97%B4.md)

[相关参数说明](https://learn.lianglianglee.com/%E4%B8%93%E6%A0%8F/Java%20%E6%A0%B8%E5%BF%83%E6%8A%80%E6%9C%AF%E9%9D%A2%E8%AF%95%E7%B2%BE%E8%AE%B2/35%20%20JVM%E4%BC%98%E5%8C%96Java%E4%BB%A3%E7%A0%81%E6%97%B6%E9%83%BD%E5%81%9A%E4%BA%86%E4%BB%80%E4%B9%88%EF%BC%9F-%E6%9E%81%E5%AE%A2%E6%97%B6%E9%97%B4.md)
```
调整类型卸载
-XX:+ClassUnloadingWithConcurrentMark

G1字符串排重
-XX:+UseStringDeduplication

G1设置占用百分比
-XX:InitiatingHeapOccupancyPercent

打印GC日志
-XX:+PrintGCDetails
-XX:+PrintGCDateStamps

// 打印G1 Ergonomics相关信息
-XX:+PrintAdaptiveSizePolicy

并行引用处理
-XX:+PrintReferenceGC

 JIT 编译的代码是存储在 Code Cache 中的，需要注意的是 Code Cache 是存在大小限制的，而且不会动态调整
-XX:ReservedCodeCacheSize=<SIZE>

关闭偏斜锁
-XX:-UseBiasedLocking
```

## 垃圾收集器
- Shenandoah通过读屏障和"Brooks Pointers"解决并发回收
- ZGC 是一款基于 Region 内存布局，(暂时)不设分代，使用读屏障、染色指针和内存多重映射等技术来实现的可并发的标记-整理算法的垃圾收集器。ZGC的Region其实被称为ZPage，具有动态性——动态创建和销毁，以及动态的区域容量大小
