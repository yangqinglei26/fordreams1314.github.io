---
title: Redis
date: 2021-06-10 19:24:06
tags:
  - java
  - redis
  - 缓存
category:
  - java
  - 缓存
---

> [基础教程](https://www.runoob.com/redis/redis-stream.html) [操作](https://www.processon.com/view/60d18761e0b34d05006ca1b5?fromnew=1#map)
>
> [基本数据类型底层实现](https://www.cnblogs.com/MouseDong/p/11134039.html)
>
> [基础框架](https://www.processon.com/view/6059480e07912927bd732d1c#map)
>
> [进阶1](https://www.processon.com/view/6007f102e0b34d45d1658090?fromnew=1#map) [进阶2](https://www.processon.com/view/6083e8b97d9c0811840540ec?fromnew=1#map) [进阶3](https://www.processon.com/view/5ea7a58807912948b0e1aa2f?fromnew=1#map)
>
> [一致性hash算法](https://blog.csdn.net/wuxiaolongah/article/details/107327803)
>
> [redis cluster1](https://www.jianshu.com/p/ab9aaae8b7e8) [redis cluster2](https://www.cnblogs.com/xuwc/p/8900717.html)
>
> [缓存穿透](https://blog.csdn.net/wuxiaolongah/article/details/106968601)
>
> [分布式锁](https://blog.csdn.net/wuxiaolongah/article/details/107006954)
>
> [跳跃表](https://www.cnblogs.com/MouseDong/p/11276198.html)
>
> [红黑树](https://www.cnblogs.com/MouseDong/p/11276211.html)
>
> [Redis与Mysql双写一致性方案解析](https://www.cnblogs.com/liuqingzheng/p/11080680.html)

## 1. 安装

## 2. 基本命令

## 3. 数据类型（5+3）

## 4. 高级特性

### 4.1. 发布和订阅

### 4.2. 管道技术

### 4.3. Stream

## 5. 事务

## 6. 内存回收

### 6.1. 过期策略

- 定时过期
- 惰性过期
- 定期过期

### 6.2. 淘汰策略

1. lru

   - volatile-lru -> Evict using approximated LRU, only keys with an expire set.
   - allkeys-lru -> Evict any key using approximated LRU.
2. lfu

   - volatile-lfu -> Evict using approximated LFU, only keys with an expire set.
   - allkeys-lfu -> Evict any key using approximated LFU.
3. random

   - volatile-random -> Remove a random key having an expire set.
   - allkeys-random -> Remove a random key, any key.
4. noeviction -> Don't evict anything, just return an error on write operations.
5. volatile-ttl -> Remove the key with the nearest expire time (minor TTL)

## 7. 持久化



## 8. 集群

### 8.1. 主从复制

- 主节点 redis.conf

```xml
bind * -::*
port 6379
daemonize yes
pidfile /usr/local/bin/redisconfigs/redis-6379/redis.pid
logfile "/usr/local/bin/redisconfigs/redis-6379/redis.log"
dir /usr/local/bin/redisconfigs/redis-6379
```

- 从节点  redis.conf

```xml
port 6381
daemonize yes
pidfile /usr/local/bin/redisconfigs/redis-6381/redis.pid
logfile "/usr/local/bin/redisconfigs/redis-6381/redis.log"
dir /usr/local/bin/redisconfigs/redis-6381
```

```
# 查看主从信息
redis-cli -p 6381 info replication
```



### 8.2. 主从+哨兵

```xml
port 26379
pidfile /usr/local/bin/redisconfigs/sentinel-26379/redis-sentinel.pid
logfile "/usr/local/bin/redisconfigs/sentinel-26379/redis-sentinel.log"
dir /usr/local/bin/redisconfigs/sentinel-26379
sentinel monitor mymaster 127.0.0.1 6379 2
```

```
# 查看哨兵信息
redis-cli -p 26379 info
```



### 8.3. redis cluster



## 面试相关

