# Spring
```
从软件工程的角度谈谈对Spring理解 软件本质是个产品，然后产品的背后是行业。一个行业就会有产品上下游，Spring属于上游的工业产品。 但是常规的业务需求，语言并不能直接满足，因为太底层，需更加具体的机器才能满足。
1. Java是纯面向对象语言
2. Spring直接提供管理类的IOC容器和修改类的AOP切面
3. 再提供面对企业需求的工具，比如Batch、Security、Cloud等等，这些能直接解决业务需求的框架
4. 然后Spring再提供一些微服务、分布式的组件，来直接提供应用的建设方案，Eureka、Config等
5. 对于Spring自行无法提供的，就通过Boot继承第三方中间件，例如Redis、Mysql、ZooKeeper 这些更高层次的抽象，能直接帮助我们建设应用，也就应Spring的广告词“提供一站式解决方案”。
```

## Spring IOC容器原理
1. IOC概念

```
(1)控制反转思想
原本是由开发人员维护和创建对象，转变为依靠Spring容器来控制对象。控制反转的本质是对象的控制权转移从开发人员转移到对象容器。

(2)软件工程理论中的六大设计原则
单一职责原则：不存在多余一个的因素导致类的状态发生变更，即一个类只负责一项单一的职责
里氏替换原则：基类出现的地方都可以用子类进行替换，而不会引起任何的不适
接口隔离原则：客户端不应该依赖于其不需要的接口，类间的依赖关系应该建立在最小的接口之上
迪米特法则：一个对象对其他对象有最少的了解
开闭原则：软件设计对于模块扩展是开放的和修改是封闭的
依赖倒置原则：高层次模块不应该依赖于低层次的模块，应该依赖于抽象
```
2.Spring IOC 的实现方式
```
```
3. Spring IOC实现原理解析
4. Spring IOC Bean 生命周期

## Spring AOP原理 

## Spring 事务管理
## 代理模式
- 静态代理
- JDK动态代理
- CGLib动态代理

## Spring Bean 常用注解
1. @Autowired
- @Autowired自动装配对象到属性，通常采用构造注入的方式能避免warning
- @Resource是Java注解
2. 自动装配
以下注解被标识的类会被Spring扫描，加入IOC容器
- @Component ：通用的注解，可标注任意类为 Spring 组件。如果一个 Bean 不知道属于哪个层，可以使用@Component 注解标注。
- @Repository : 对应持久层即 Dao 层，主要用于数据库相关操作。
- @Service : 对应服务层，主要涉及一些复杂的逻辑，需要用到 Dao 层。
- @Controller : 对应 Spring MVC 控制层，主要用于接受用户请求并调用 Service 层返回数据给前端页面。 
3. Bean 的作用域
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

## 配置化参数
1. @Value("${}") 简单读取配置文件数据
2. @ConfigurationProperties()读取配置文件中数据对应赋值到一个类中

## Spring 事务
5. Spring事务的七个传播级别

3.1 Spring事务失效的原因
- 不是public
- 类自身方法调用
- 异常:异常没被捕获或者异常被提前捕获
- 多线程
- 不是Spring容器管理的类

3.1 Spring事务的隔离级别 3.2  

## Spring环境属性源
1. JVM系统属性
2. 操作系统环境变量
3. 命令行参数
4. 应用属性配置文件（Application.properties,Application.yaml）
5. 中心化的配置服务器






