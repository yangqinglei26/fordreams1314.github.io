---
title: Java
date: 2021-05-28 19:24:06
updated: 2021-06-01 19:24:06
tags:
  - java	
  - jvm
  - juc
category:
  - java	
  - jvm
  - juc
---

## 1. IO和NIO

## 2. 多线程

### 2.1. 线程的创建

#### 2.1.1. 实现Runnable接口

> 推进使用：方便同一个对象被多个线程使用
>

```java
new Thread(Runnable 实现).start()
```

#### 2.1.2. 继承Thread

#### 2.1.3. 实现Callable接口

```
实现Callable接口，需要返回值类型
重写call方法，需要抛出异常
创建目标对象
创建执行服务：ExecutorService ser = Executors.newFixedThreadPool(1);
提交执行：Future<Boolean> result1 = ser.submit(t1);
获取结果：boolean r1 = result1.get()
关闭服务：ser.shutdownNow()
```

## 3. 注解和反射

## 4. JUC

## 5. JVM

