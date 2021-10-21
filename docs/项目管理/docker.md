## docker
### 一次性操作所有容器的命令
- docker中 启动所有的容器命令
  `docker start $(docker ps -a | awk '{ print $1}' | tail -n +2)`
- docker中 关闭所有的容器命令
  `docker stop $(docker ps -a | awk '{ print $1}' | tail -n +2)`
- docker中 删除所有的容器命令
  `docker rm $(docker ps -a | awk '{ print $1}' | tail -n +2)`
- docker中 删除所有的镜像
  `docker rmi $(docker images | awk '{print $3}' |tail -n +2)`

