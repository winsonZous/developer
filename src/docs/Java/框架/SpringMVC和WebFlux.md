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

#### 前后端传值注解







## WebFlux


