# web后端框架

## SpringMVC

在SpringBoot中SpringMVC被封装成RestFul Web模块，不再使用Modol and View模式。 实现http接口的主要区别是把Java对象处理JSON添加到Http的响应报文里面。

- SpringMVC的请求流程

## 前置知识Servlet,springboot内置的tomcat本质是个servlet容器

### servlet生命周期
- Servlet 初始化后调用 init () 方法。
```
init() 方法简单地创建或加载一些数据，这些数据将被用于 Servlet 的整个生命周期。
```
- Servlet 调用 service() 方法来处理客户端的请求。
```
service() 方法是执行实际任务的主要方法。Servlet 容器（即 Web 服务器）调用 service() 方法来处理来自客户端（浏览器）的请求，并把格式化的响应写回给客户端。
每次服务器接收到一个 Servlet 请求时，服务器会产生一个新的线程并调用服务。service() 方法检查 HTTP 请求类型（GET、POST、PUT、DELETE 等
```
- Servlet 销毁前调用 destroy() 方法。
```
destroy() 方法可以让 Servlet 关闭数据库连接、停止后台线程、把 Cookie 列表或点击计数器写入到磁盘，并执行其他类似的清理活动。
```

### HTTP 请求类型

#### 5 种常见的请求类型:

- GET : 请求从服务器获取特定资源。举个例子：GET /users（获取所有学生）
- POST : 在服务器上创建一个新的资源。举个例子：POST /users（创建学生）
- PUT : 更新服务器上的资源（客户端提供更新后的整个资源）。举个例子：PUT /users/12（更新编号为 12 的学生）
- DELETE : 从服务器删除特定的资源。举个例子：DELETE /users/12（删除编号为 12 的学生）
- PATCH : 更新服务器上的资源（客户端提供更改的属性，可以看做作是部分更新），使用的比较少，这里就不举例子了。

#### 常用注解

- @RestController=@Controller + @ResponseBody

## SpringBoot Web模块与Http Client

Java社区中的Http Client

- JDK的 HttpUrlConnection
- Apache commons的HttpClient
- Square公司的okHttp
- Spring Web 模块的ResTemplate

这些都是实现http协议的优秀框架，不过http本身也有许多缺点

###SpringMVC 前后端传值
- 路径参数`@PathVariable`
- 请求参数`@RequestParam`
- 请求体参数`@RequestBody`


- validation的分组校验参数校验
1. spring-boot-starter-validation 会加入 hibernate-validator
2. 常用参数注解
   @NotEmpty 被注释的字符串的不能为 null 也不能为空
   @NotBlank 被注释的字符串非 null，并且必须包含一个非空白字符
   @Null 被注释的元素必须为 null
   @NotNull 被注释的元素必须不为 null
   @AssertTrue 被注释的元素必须为 true
   @AssertFalse 被注释的元素必须为 false
   @Pattern(regex=,flag=)被注释的元素必须符合指定的正则表达式
   @Email 被注释的元素必须是 Email 格式。
   @Min(value)被注释的元素必须是一个数字，其值必须大于等于指定的最小值
   @Max(value)被注释的元素必须是一个数字，其值必须小于等于指定的最大值
   @DecimalMin(value)被注释的元素必须是一个数字，其值必须大于等于指定的最小值
   @DecimalMax(value) 被注释的元素必须是一个数字，其值必须小于等于指定的最大值
   @Size(max=, min=)被注释的元素的大小必须在指定的范围内
   @Digits (integer, fraction)被注释的元素必须是一个数字，其值必须在可接受的范围内
   @Past被注释的元素必须是一个过去的日期
   @Future 被注释的元素必须是一个将来的日期


### 优秀的 HTTP Client 需要具备的特性

- 连接池 HTTP 1.1 不支持多路复用，只有 HTTP Pipeline 这用半复用的模型支持。
- 超时时间设置（连接超时、读取超时等）当对端出现问题的时候，长时间的，甚至是无限的超时等待是绝对不能接受的。所以必须必须能够设置超时时间。
- 是否支持异步 即使HTTP 协议栈是基于非阻塞 IO 实现的，调用客户端的或者在服务端处理消息的线程有大量时间被浪费在了等待 IO 上面。
- 请求和响应的编解码 http框架主要是帮助开发者降低对网络协议的编码和解码的工作
- 可扩展性 能否自定义读写消息的格式转换，异常处理

#### 前后端传值注解



