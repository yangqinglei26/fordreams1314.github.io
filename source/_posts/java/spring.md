---
title: Spring
date: 2021-06-08 19:24:06
tags:
  - java
  - spring
category:
  - java
  - spring
---

> [spring](https://snailclimb.gitee.io/javaguide/#/docs/system-design/framework/spring/Spring%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98%E6%80%BB%E7%BB%93?id=_7-spring-%e6%a1%86%e6%9e%b6%e4%b8%ad%e7%94%a8%e5%88%b0%e4%ba%86%e5%93%aa%e4%ba%9b%e8%ae%be%e8%ae%a1%e6%a8%a1%e5%bc%8f%ef%bc%9f)

## IOC

> [Spring IOC 容器源码分析](https://javadoop.com/post/spring-ioc)

- bean的注解

  - @Component @Controller @Service @Repository
  - @Bean 作用于方法

- bean的作用域

  - singleton prototype request session

- bean的生命周期

  > [SpringBean生命周期详解](https://blog.csdn.net/weixin_43244698/article/details/109338537)
  >
  > [Spring Bean的生命周期](https://www.cnblogs.com/zrtqsk/p/3735273.html)

  - beandefinition --->  BeanFactoryPostProcessor.postProcessBeanFactory() 修改beandefinition ---> InstantiationAwareBeanPostProcessorAdapter .postProcessBeforeInstantiation() ---> 实例化 --->InstantiationAwareBeanPostProcessorAdapter .postProcessAfterInstantiation() ---> InstantiationAwareBeanPostProcessorAdapter .postProcessProperties() 修改property ---> 配置property --->

    检查aware接口并设置相关依赖 ---> init()  ---> destroy()

- 单例bean的线程安全

  - ThreadLocale
  - prototype

## AOP

> [JDK动态代理](https://www.cnblogs.com/zuidongfeng/p/8735241.html) [动态代理与静态代理区别](https://blog.csdn.net/ikownyou/article/details/53081426)
>
> [AspectJ的使用方法](https://blog.csdn.net/babylovewei/article/details/106528284)    [Spring AOP和AspectJ的区别是什么？](https://www.cnblogs.com/chaoesha/p/13037368.html)

## spring mvc

## spring 事务

> [事务相关](https://snailclimb.gitee.io/javaguide/#/docs/system-design/framework/spring/Spring%E4%BA%8B%E5%8A%A1%E6%80%BB%E7%BB%93?id=_5-transactional-%e7%9a%84%e4%bd%bf%e7%94%a8%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9%e6%80%bb%e7%bb%93)
>
> [一口气说出 6种 @Transactional 注解失效场景](https://mp.weixin.qq.com/s?__biz=Mzg2OTA0Njk0OA==&mid=2247486483&idx=2&sn=77be488e206186803531ea5d7164ec53&chksm=cea243d8f9d5cacecaa5c5daae4cde4c697b9b5b21f96dfc6cce428cfcb62b88b3970c26b9c2&token=816772476&lang=zh_CN#rd)

**`@Transactional` 的常用配置参数总结（只列巨额 5 个我平时比较常用的）：**

| 属性名      | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| propagation | 事务的传播行为，默认值为 REQUIRED，可选的值在上面介绍过      |
| isolation   | 事务的隔离级别，默认值采用 DEFAULT，可选的值在上面介绍过     |
| timeout     | 事务的超时时间，默认值为-1（不会超时）。如果超过该时间限制但事务还没有完成，则自动回滚事务。 |
| readOnly    | 指定事务是否为只读事务，默认值为 false。                     |
| rollbackFor | 用于指定能够触发事务回滚的异常类型，并且可以指定多个异常类型。 |

**@Transactional的使用注意事项总结**

1. `@Transactional` 注解只有作用到 public 方法上事务才生效，不推荐在接口上使用；
2. 避免同一个类中调用 `@Transactional` 注解的方法，这样会导致事务失效；
3. 正确的设置 `@Transactional` 的 rollbackFor 和 propagation 属性，否则事务可能会回滚失败

## spring 设计模式

> [设计模式](https://snailclimb.gitee.io/javaguide/#/docs/system-design/framework/spring/Spring-Design-Patterns?id=%e8%a3%85%e9%a5%b0%e8%80%85%e6%a8%a1%e5%bc%8f)

- **工厂设计模式** : Spring使用工厂模式通过 `BeanFactory`、`ApplicationContext` 创建 bean 对象。
- **代理设计模式** : Spring AOP 功能的实现。
- **单例设计模式** : Spring 中的 Bean 默认都是单例的。
- **模板方法模式** : Spring 中 `jdbcTemplate`、`hibernateTemplate` 等以 Template 结尾的对数据库操作的类，它们就使用到了模板模式。
- **包装器设计模式** : 我们的项目需要连接多个数据库，而且不同的客户在每次访问中根据需要会去访问不同的数据库。这种模式让我们可以根据客户的需求能够动态切换不同的数据源。
- **观察者模式:** Spring 事件驱动模型就是观察者模式很经典的一个应用。
- **适配器模式** :Spring AOP 的增强或通知(Advice)使用到了适配器模式、spring MVC 中也是用到了适配器模式适配`Controller`。

## 循环依赖

> [循环依赖的解决](https://www.jianshu.com/p/6c359768b1dc) [Spring 是如何解决循环依赖的](https://www.zhihu.com/question/438247718/answer/1730527725)
>
> [核心](https://mp.weixin.qq.com/s/kS0K5P4FdF3v-fiIjGIvvQ)

**循环依赖问题解决方法很多，主要有：**

1. 使用`@Lazy`注解，延迟加载
2. 使用`@DependsOn`注解，指定加载先后关系
3. 修改文件名称，改变循环依赖类的加载顺序

