# Docker

查看所有容器           `docker ps -a`
进入容器              `docker exec -it [container id] /bin/bash` (-it 交互式终端)
停用全部运行中容器      `docker stop $(docker ps -q)`
删除全部容器           `docker rm $(docker ps -aq)`
停用并删除容器         `docker stop $(docker ps -q) & docker rm $(docker ps -aq)`
启动容器并且后台运行    `docker run --name node -dit node:latest`
删除所有镜像           `docker rmi $(docker images -q)`
复制文件              `docker cp /opt/local/file.txt mycontainer:/opt/`
容器使用多个端口       `docker run -p 22:33 -p 200:230 image`
公开一串端口          `docker run -it -p 7100-7120:7100-7120/tcp `
提交更改              `docker commit -a "wangshibo" -m "this is test" 651a8541a47d myubuntu:v1`
