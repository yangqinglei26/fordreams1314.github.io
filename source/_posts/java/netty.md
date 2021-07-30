---
title: netty
date: 2021-05-29 19:24:06
tags:
  - java
  - 消息队列
  - rabbitmq
category:
  - java
  - 消息队列
---

> [TCP/IP协议](https://www.cnblogs.com/crazymakercircle/p/14499211.html) [TCP相关](https://my.oschina.net/u/1859679/blog/1835423) [socket原理](https://blog.csdn.net/pashanhu6402/article/details/96428887)
>
> [单服务器最大tcp连接数及调优汇总](https://www.cnblogs.com/duanxz/p/4464178.html) [分析单机最大长连接数](https://blog.csdn.net/xielinrui123/article/details/88417225)
>
> [IO多路复用机制详解](https://blog.csdn.net/baixiaoshi/article/details/48708347?utm_source=copy) [io相关](https://www.cnblogs.com/crazymakercircle/p/10225159.html)
>
> [Reactor详解](https://my.oschina.net/u/1859679/blog/1844109) [Reactor模式](https://www.cnblogs.com/crazymakercircle/p/9833847.html) [理解高性能网络模型](https://www.jianshu.com/p/2965fca6bb8f)
>
> [netty相关](https://www.cnblogs.com/lighten/tag/Netty/)
>
> [面试相关](https://www.cnblogs.com/crazymakercircle/p/13903625.html)

## 1. 线程模型



## 2. 核心组件



## 3. 零拷贝

> [彻底搞懂Netty高性能之零拷贝](https://www.jianshu.com/p/e488c8ee5b57)

- Netty的接收和发送ByteBuffer使用直接内存进行Socket读写，不需要进行字节缓冲区的二次拷贝。如果使用JVM的堆内存进Socket读写，JVM会将堆内存Buffer拷贝一份到直接内存中，然后才写入Socket中。相比于使用直接内存，消息在发送过程中多了一次缓冲区的内存拷贝。
- Netty的文件传输调用FileRegion包装的transferTo方法，可以直接将文件缓冲区的数据发送到目标Channel，避免通过循环write方式导致的内存拷贝问题。
- Netty提供CompositeByteBuf类, 可以将多个ByteBuf合并为一个逻辑上的ByteBuf, 避免了各个ByteBuf之间的拷贝。
- 通过wrap操作, 我们可以将byte[]数组、ByteBuf、ByteBuffer等包装成一个Netty ByteBuf对象, 进而避免拷贝操作。
- ByteBuf支持slice操作，可以将ByteBuf分解为多个共享同一个存储区域的ByteBuf, 避免内存的拷贝。

## 4. TCP粘包/拆包

> [[Netty中粘包和拆包的解决方案]](https://www.cnblogs.com/coding-diary/p/11650686.html)
>
> [Netty解决粘包和拆包问题的四种方案](https://blog.csdn.net/lanzhupi/article/details/88929432)

## 5. 编码和解码



## 6. 多协议



## 7. 心跳

> [Netty实现心跳机制与断线重连](https://www.jianshu.com/p/1a28e48edd92)

