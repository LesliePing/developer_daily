# Docker

查看所有容器           `docker ps -a`
进入容器              `docker exec -it [container id] /bin/bash` (-it 交互式终端)
停用全部运行中容器      `docker stop $(docker ps -q)`
删除全部容器           `docker rm $(docker ps -aq)`
停用并删除容器         `docker stop $(docker ps -q) & docker rm $(docker ps -aq)`
