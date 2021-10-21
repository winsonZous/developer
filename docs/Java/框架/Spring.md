# Spring

从软件工程的角度谈谈对Spring理解 软件本质是个产品，然后产品的背后是行业。一个行业就会有产品上下游，Spring属于上游的工业产品。 但是常规的业务需求，语言并不能直接满足，因为太底层，需更加具体的机器才能满足。

1. Java是纯面向对象语言
2. Spring直接提供管理类的IOC容器和修改类的AOP切面
3. 再提供面对企业需求的工具，比如Batch、Security、Cloud等等，这些能直接解决业务需求的框架
4. 然后Spring再提供一些微服务、分布式的组件，来直接提供应用的建设方案，Eureka、Config等
5. 对于Spring自行无法提供的，就通过Boot继承第三方中间件，例如Redis、Mysql、ZooKeeper 这些更高层次的抽象，能直接帮助我们建设应用，也就应Spring的广告词“提供一站式解决方案”。

## IOC
1. Java是纯面向对象语言，完成一个功能需要多个对象协作，就会存在对象间关系。 这些关系包括依赖，关联，聚合，组合。IOC容器本质就是为了解决对象间耦合的问题。
2. 容器创建
3. Bean生命周期
4. Bean循环依赖问题
5. Bean 的作用域

`
@Scope
声明 Spring Bean 的作用域，使用方法:

@Bean
@Scope("singleton")
   public Person personSingleton() {
   return new Person();
}
四种常见的 Spring Bean 的作用域：

singleton : 唯一 bean 实例，Spring 中的 bean 默认都是单例的。
prototype : 每次请求都会创建一个新的 bean 实例。
request : 每一次 HTTP 请求都会产生一个新的 bean，该 bean 仅在当前 HTTP request 内有效。
session : 每一次 HTTP 请求都会产生一个新的 bean，该 bean 仅在当前 HTTP session 内有效。
`


## AOP切面
1. 


## 常用注解
1. 自动注入 @Autowired和@Resource
2. 标识Bean，并且把Bean注入容器 2.1 Service 2.2 Controller 2.3 Repository 2.4 Component 2.5 Bean
   使用第三方类库的时候无法添加注解把Bean加入容器,可以通过该注解加在方法上。 同时可以实现类似OnConditional的功能。

3. Spring事务的七个传播级别

3.1 Spring事务失效的原因

- 不是Spring容器管理的类
- 不是public方法也没有用AspectJ
- 类自身方法调用
- 异常:异常没被捕获或者异常被提前捕获

3.1 Spring事务的隔离级别 3.2  





