# Docker

## 安装
1.https://www.docker.com/get-started/
[参考]2.https://www.modb.pro/db/104969
[参考]3.https://www.cnblogs.com/wanglei957/p/11819547.html
[参考]4.节点宕机：https://www.cnblogs.com/wangbiaohistory/p/14638935.html

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


数据库运行            `docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql`
集群全部司机（主机宕机）`vim /var/lib/mysql/grastate.dat 修改 sate_to_bootstrap=1`
## 创建第1个MySQL节点
`docker run -d --name=mysql-node1 -p 3310:3306 --privileged=true -e MYSQL_ROOT_PASSWORD=123456 -e CLUSTER_NAME=PXC -e XTRABACKUP_PASSWORD=abc123456 -v v1:/var/lib/mysql --net=net1 --ip 172.18.0.2 pxc`

## 创建第2个MySQL节点
`docker run -d --name=mysql-node2 -p 3311:3306 --privileged=true -e MYSQL_ROOT_PASSWORD=123456 -e CLUSTER_NAME=PXC -e XTRABACKUP_PASSWORD=abc123456 -e CLUSTER_JOIN=mysql-node1 -v v2:/var/lib/mysql --net=net1 --ip 172.18.0.3 pxc`
## 创建haproxy用户
`create user 'haproxy'@'%' identified by '';`
`docker run -it -d --name haproxy-node1 -p 4001:8888 -p 4002:3306 --restart always --privileged=true -v /home/apps/haproxy:/usr/local/etc/haproxy --net=net1 --ip 172.18.0.7 haproxy:2.3.13`

`haproxy -f /usr/local/etc/haproxy/haproxy.cfg`
