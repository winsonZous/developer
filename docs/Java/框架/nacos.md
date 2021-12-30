# nacos

## nacos

- 动态刷新配置

```
原理@NacosValue 通过后置处理器 ApplicationEvent
```

- 回退历史版本

## docker 安装nacos

1. docker search nacos
2. docker pull nacos/nacos-server
3. docker run -d -p 8848:8848 --env MODE=standalone --name nacos nacos/nacos-server

## springboot集成nacos

```
（1）增加依赖
        <dependency>
            <groupId>com.alibaba.boot</groupId>
            <artifactId>nacos-config-spring-boot-starter</artifactId>
            <version>0.2.6</version>
        </dependency>
（2）增加配置
nacos:
  config:
    bootstrap:
      enable: true
    # 主配置服务器地址
    server-addr: 39.103.194.101:8848
    # 主配置 data-id
    data-id: stock-manager
    # 主配置 group-id
    group: stock
    # 命名空间
    namespace: dev
    # 主配置 配置文件类型
    type: yaml
    # 主配置 最大重试次数
    max-retry: 10
    # 主配置 开启自动刷新
    auto-refresh: true
    # 主配置 重试时间
    nconfig-retry-time: 2333
    # 主配置 配置监听长轮询超时时间
    config-long-poll-timeout: 46000
    # 主配置 开启注册监听器预加载配置服务（除非特殊业务需求，否则不推荐打开该参数）
    enable-remote-sync-config: true

```

##### 参考nacos官网https://nacos.io/zh-cn/docs/quick-start-spring-boot.html