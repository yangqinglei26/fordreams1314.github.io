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

### 2.1. 创建线程

#### 2.1.1. 实现Runnable接口

> 推进使用：方便同一个对象被多个线程使用

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

### 2.2. 停止线程

#### 2.2.1. 设置一个标志位

```java
publ
```

### 2.3. 礼让线程

> yield()

- 礼让线程，让当前正在执行的线程暂停，但不阻塞
- 将线程从运行状态转为就绪状态
- 让cpu重新调度，礼让不一定成功！看cpu心情

### 2.4. 强制执行线程

> join()

### 2.5. 线程优先级

> priority(1-10)

- 先设置优先级，再start()

### 2.6. 守护线程

### 2.7. 线程同步

- 队列+锁

- synchronized 
- lock

### 2.8. 线程通信

- 生产者和消费者问题
- synchronized 
- while 防止虚假唤醒

- wait()、notifyall()

#### 2.8.1. 管程法

- 缓冲池

#### 2.8.2. 信号灯法

- 标志位

### 2.9. 线程池



## 3. 注解和反射

## 4. JUC

### 4.1. wait和sleep的区别

- 来自不同的类

wait => object    sleep => Thread

- 锁的释放

wait 会释放锁，sleep 不会释放

- 使用范围

wait 在 synchronized 中使用

### 4.2. Lock锁

#### 4.2.1. ReentrantLock

- 默认非公平锁

#### 4.2.3. synchronized 和 lock 的区别

| 序号 | synchronized                   | lock                 |
| ---- | ------------------------------ | -------------------- |
| 1    | 内置的java关键字               | java接口             |
| 2    | 无法获取锁的状态               | 可以获取锁的状态     |
| 3    | 会自动释放锁                   | 手动释放锁           |
| 4    | 线程阻塞时，其它线程会一直等待 | 可以主动尝试获取锁   |
| 5    | 非公平锁，不可以中断           | 可以自定义           |
| 6    | 适合锁少量的同步代码           | 适合锁大量的同步代码 |

#### 4.2.4. Condition

> await() 、signal()

#### 4.2.5. 八锁现象

synchronized 锁的对象

- 方法的调用者
- class类模板（static）

## 5. JVM

## 6. java8

### 6.1. lamada表达式

#### 6.1.1. 函数式接口

- 定义：任何接口，如果只包含唯一一个抽象方法，那么它就是函数式接口 
- 可以用lamada表达式代替匿名内部类来实现

