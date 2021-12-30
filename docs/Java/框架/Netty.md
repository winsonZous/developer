# Netty

## 第一部分 IO基础

### IO基础

1. Linux网络IO模型
2. IO多路复用技术

### Socket 和 ServerSocket

### 4种IO模型

1. BIO
2. 伪异步IO
3. NIO
4. AIO
5. 4种IO的对比
6. Netty优缺点

### BIO、NIO、AIO和Netty实现时间服务器的案例

1. BIO
2. NIO
3. AIO
4. Netty

### TCP拆包/粘包问题解决之道

1. TCP拆包/粘包问题说明
   ![img.png](TCP拆包粘包问题.png)
2. TCP拆包粘包问题原因

```
（1）应用程序write写入的字节大小大于套接字缓冲区大小
（2）进行MSS大小的TCP分片
（3）以太网帧的payload大于MTU进行IP分片
```

3. TCP粘包异常案例

```

```

4. LineBasedFrameDecoder解决TCP粘包问题

## 第二部分 Netty编解码开发

## 第三部分 Netty多协议开发和应用

1. Http协议开发
2. webSocket协议开发
3. UDP协议开发
4. 文件传输
5. 私有协议栈开发

## 第四部分 Netty功能介绍和源码分析

1. ByteBuf
2. Channel和Unsafe
3. ChannelPipeline和ChannelHandler
4. EventLoop和eventLoopGroup
5. Future和Promise
