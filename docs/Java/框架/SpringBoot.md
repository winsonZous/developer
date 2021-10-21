
## SpringBootApplication
```
@SpringBootApplication 是一个方便的注释，它添加了以下所有内容：
@Configuration：将类标记为应用程序上下文的 bean 定义源。
@EnableAutoConfiguration：告诉 Spring Boot 根据类路径设置、其他 bean 和各种属性设置开始添加 bean。例如，如果spring-webmvc在类路径上，此注释将应用程序标记为 Web 应用程序并激活关键行为，例如设置DispatcherServlet.
@ComponentScan：告诉 Spring 在包中查找其他组件、配置和服务com/example，让它找到控制器。
```

## 可执行Jar
```
        <plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
		通过添加maven打包插件，maven install能把启动类打包成一个可执行jar文件。
		java -jar jar包全路径就能启动
```

## SpringBoot 自动配置原理
1. 启动SpringBootApplication类
   run方法内会有new SpringApplication(primarySources).run(args);
2. 初始化容器 
   setInitializers((Collection) getSpringFactoriesInstances(
   ApplicationContextInitializer.class));
3. 加载所有Factory
   set<String> names = new LinkedHashSet<>(
   SpringFactoriesLoader.loadFactoryNames(type, classLoader));
4. 用classloader加载spring.factories文件
5. spring.factories内都是Configuration注解的配置类的路径
6. 配置类就会告诉Spring要把这些Bean加载到容器里面去



## 测试用例编写

参考: SpringBoot官方文档 https://docs.spring.io/spring-boot/docs/2.1.0.RELEASE/reference/htmlsingle/
