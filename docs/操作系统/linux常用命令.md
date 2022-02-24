# 查看网络端口占用的进程
```
netstat -nlp | grep 33676
[root@application proc]# netstat -nlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:33670           0.0.0.0:*               LISTEN      15463/docker-proxy  
```
iptables防火墙
1、基本操作

# 查看防火墙状态

service iptables status

# 停止防火墙

service iptables stop

# 启动防火墙

service iptables start

# 重启防火墙

service iptables restart

# 永久关闭防火墙

chkconfig iptables off

# 永久关闭后重启

chkconfig iptables on

2、开启80端口

vim /etc/sysconfig/iptables
# 加入如下代码
-A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
保存退出后重启防火墙

service iptables restart
二、firewall防火墙
1、查看firewall服务状态

systemctl status firewalld

出现Active: active (running)切高亮显示则表示是启动状态。

出现 Active: inactive (dead)灰色表示停止，看单词也行。
2、查看firewall的状态

firewall-cmd --state
3、开启、重启、关闭、firewalld.service服务

# 开启
service firewalld start
# 重启
service firewalld restart
# 关闭
service firewalld stop
4、查看防火墙规则

firewall-cmd --list-all
5、查询、开放、关闭端口

# 查询端口是否开放
firewall-cmd --query-port=8080/tcp
# 开放80端口
firewall-cmd --permanent --add-port=80/tcp
# 移除端口
firewall-cmd --permanent --remove-port=8080/tcp
#重启防火墙(修改配置后要重启防火墙)
firewall-cmd --reload

# 参数解释
1、firwall-cmd：是Linux提供的操作firewall的一个工具；
2、--permanent：表示设置为持久；
3、--add-port：标识添加的端口；


# 检查硬件配置
1、du -sh 查看当前目标的空间大小
2、top命令
shift+P CPU消耗大小排序
shift+M 查看消耗内存大小排序
load average 1分钟 5分钟 10分钟的负载

3、查看端口占用
netstat -nlp | grep 端口号
ps -ef | grep 进程
kill -9 进程号 （通过SIGTERM）

# 常见问题
1. kill 与kill -9 区别
```
1、kill -9 id：一般不加参数kill是使用15来杀，这相当于正常停止进程，停止进程的时候会释放进程所占用的资源；他们的区别就好比电脑关机中的软关机（通过“开始”菜单选择“关机”）与硬关机（直接切断电源），虽然都能关机，但是程序所作的处理是不一样的。
2、kill - 9 表示强制杀死该进程；而 kill 则有局限性，例如后台进程，守护进程等；
3、执行kill命令，系统会发送一个SIGTERM信号给对应的程序。SIGTERM多半是会被阻塞的。kill -9命令，系统给对应程序发送的信号是SIGKILL，即exit。exit信号不会被系统阻塞，所以kill -9能顺利杀掉进程。
```
