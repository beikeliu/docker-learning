# docker-learning
- Tip: 使用${xxx}作为占位符，用户应根据实际场景自行填入
## 三大基本概念
1. 镜像： 个人理解为装机光盘，例如 Windows XP，就是一个固定的文件，可以安装到容器里用来初始化环境。
2. 容器： 容器是镜像运行时的实体，根据镜像可以生成容器，容器是一个独立于宿主机的隔离进程，并且有属于容器自己的网络和命名空间。
3. 仓库： 用来存储镜像的仓库，个人理解类似于npm包管理这样。

## 镜像加速
```sh
# Docker Engine
{
  "registry-mirrors": [
    "https://hub-mirror.c.163.com",
    "https://mirror.baidubce.com"
  ]
}
```
## 镜像命令
```sh
# 获取
docker pull ubuntu:18.04
# 单次运行(运行后exit即销毁)
docker run -it --rm ubuntu:18.04 bash
# 列出
docker image ls
# 删除
docker image rm ${123456}
# 清理虚悬镜像(因为某些更新问题导致丢失版本的临时镜像文件)
docker image prune
```

## 容器命令
```sh
# 创建容器
docker run --name ${webserver} -d -p ${80:80} ${nginx}
# 进入容器
docker exec -it ${webserver} bash
# 列出
docker container ls
# 启动已停止容器
docker container start ${123456}
# 重启容器
docker container restart ${123456}
# 删除容器
docker container rm ${123456}
# 清理所有终止状态下容器
docker container prune
```
