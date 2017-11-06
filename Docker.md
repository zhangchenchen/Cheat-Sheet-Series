## 镜像类

```bash
docker build --rm=true . 构建镜像
docker pull ${IMAGE} 安装镜像
docker images 显示已经安装的镜像
docker images --no-trunc 显示已经安装镜像的详细内容
docker rmi ${IMAGE_ID} 删除指定镜像
docker rmi $(docker images | grep “^” | awk “{print $3}”) 删除所有没有标签的镜像
docker rm $(docker ps -aq) 删除所有的镜像
docker rmi $(docker images --quiet --filter &quot;dangling=true&quot;) 删除未使用的镜像
```

## 容器类

docker run 运行容器
docker ps 显示正在运行的容器
docker ps -a 显示所有的容器
docker stop ${CID} 停止指定容器
docker stop docker ps -q 停止所有正在运行的容器
docker ps -a --filter &quot;exited=1&quot; 显示所有退出状态为1的容器
docker rm ${CID} 删除指定容器
docker ps -a | grep wildfly | awk '{print $1}' | xargs docker rm -f 使用正则表达式删除容器
docker rm -f $(docker ps -a | grep Exit | awk '{ print $1 }') 删除所有退出的容器
docker rm $(docker ps -aq) 删除所有的容器
docker inspect --format '{{ .NetworkSettings.IPAddress }}' ${CID} 显示指定容器的IP
docker attach ${CID} 进入容器
docker exec -it ${CID} bash 进入容器打开一个shell
docker ps | grep wildfly | awk '{print $1}' 通过正则表达式查找容器的镜像ID