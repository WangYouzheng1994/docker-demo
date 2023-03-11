#### Docker file



#### docker-compose
1. services和project
> 一个services包含了许多的docker image，在docker compose中 一个image就是一个project

2. 简单的docker-compose.yml解析
```
version: "3"

services:
  microService:
    image: mydocker_image:1.1
    container_name: mdc:0.0.1
    ports:
      - "9888:1024"
    volumes:
      - /opt/docker/mydocker_image:/data
    networks:
      - abc
```
> 以上compose编排等价于
```
docker run -d -p 9888:1024 -v /opt/docker/mydocker_image:/data --network mynet --name mdc:0.0.1 mydocker_image:1.1

后台运行mydocker_image:1.1镜像，
将宿主机9888端口映射给容器1024端口，
设置数据卷：把宿主机的/opt/docker/mydocker_image目录 映射给容器中的/data
设置网络为 mynet
设置容器名字为 mdc版本0.0.1

```
