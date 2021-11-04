#Spring中Http接口的实现

## SpringMVC
在SpringBoot中SpringMVC被封装成RestFul Web模块，不再使用Modol and View模式。
实现http接口的主要区别是把Java对象处理JSON添加到Http的响应报文里面。

###HTTP 请求类型
####5 种常见的请求类型:
- GET : 请求从服务器获取特定资源。举个例子：GET /users（获取所有学生）
- POST : 在服务器上创建一个新的资源。举个例子：POST /users（创建学生）
- PUT : 更新服务器上的资源（客户端提供更新后的整个资源）。举个例子：PUT /users/12（更新编号为 12 的学生）
- DELETE : 从服务器删除特定的资源。举个例子：DELETE /users/12（删除编号为 12 的学生）
- PATCH : 更新服务器上的资源（客户端提供更改的属性，可以看做作是部分更新），使用的比较少，这里就不举例子了。

#### 常用注解
- @RestController
`
  @RestController=@Controller + @ResponseBody  
`
- 

## SpringBoot Web模块与Http Client
Java社区中的Http Client 
- JDK的 HttpUrlConnection 
- Apache commons的HttpClient 
- Square公司的okHttp
- Spring Web 模块的ResTemplate

这些都是实现http协议的优秀框架，不过http本身也有许多缺点
### 优秀的 HTTP Client 需要具备的特性
- 连接池 HTTP 1.1 不支持多路复用，只有 HTTP Pipeline 这用半复用的模型支持。
- 超时时间设置（连接超时、读取超时等）当对端出现问题的时候，长时间的，甚至是无限的超时等待是绝对不能接受的。所以必须必须能够设置超时时间。
- 是否支持异步 即使HTTP 协议栈是基于非阻塞 IO 实现的，调用客户端的或者在服务端处理消息的线程有大量时间被浪费在了等待 IO 上面。
- 请求和响应的编解码 http框架主要是帮助开发者降低对网络协议的编码和解码的工作
- 可扩展性 能否自定义读写消息的格式转换，异常处理
#### 前后端传值注解







## WebFlux


