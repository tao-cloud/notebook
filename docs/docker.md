## 



## docker 常用命令



### 镜像命令



```shell
[root@VM-0-10-centos ~]# docker images
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
hello-world   latest    bf756fb1ae65   13 months ago   13.3kB
[root@VM-0-10-centos ~]#
```

**docker search** =搜索

```shell

NAME                              DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
mysql                             MySQL is a widely used, open-source relation…   10435     [OK]
mariadb                           MariaDB is a community-developed fork of MyS…   3874      [OK]

```

**docker pull 下载镜像**



**docker rmi -f ** 删除镜像



### 容器命令

---

说明:有了镜像才可以创建容器

**新建容器并启动**

```shell
docker run [] image
# 参数说明
--name="Name"			容器名字  tomcat1 tomcat2
-d								后台方式运行
-it								使用交互方式运行
-p								置顶容器端口 -p	8080:8080
-P								

ot@VM-0-10-centos ~]# docker run -it centos /bin/bash  

# 从容器退出主机
exit

# 列出所有运行的容器
[root@VM-0-10-centos /]# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
[root@VM-0-10-centos /]# docker ps -a
CONTAINER ID   IMAGE          COMMAND       CREATED             STATUS                          PORTS     NAMES
dd30a49e1680   centos         "/bin/bash"   2 minutes ago       Exited (0) About a minute ago             happy_joliot
fec663768f2a   bf756fb1ae65   "/hello"      About an hour ago   Exited (0) About an hour ago              mystifying_allen
[root@VM-0-10-centos /]#
```

**删除容器**

```shell
docker rm 容器id		#不能删除正在运行容器
docker rm -f $(docker ps -aq) #删除所有容器
docker ps -a -q|xargs docker rm		#删除所有容器
```

**启动停止容器**

```shell
docker start	容器id				# 启动容器

```



### 常用其他命令

**后台启动容器**

```shell
# 命令
[root@VM-0-10-centos /]# docker run -d centos
# 问题 docker ps ,发现centos 停止了

# 常见的坑,docker 容器使用后台运行,就必须要有一个前台进程

```

**查看日志命令**

```shell
docker logs -f -t --tail 容器
```



### 作业

> Docker 安装 nginx 

```shell
# 1.搜索镜像 search
#	2.下载镜像 pull
# 3.运行测试
# -d 后台运行
# --name 容器名字
# -p 宿主机端口:容器端口
[root@VM-0-10-centos /]# docker run -d --name nginx01 -p 3344:80 nginx
c6119f4d8eb2f4a9973c5f8a6f9f10d2690f57e2682b82e17187cdaee8b5de2b
[root@VM-0-10-centos /]# docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
c6119f4d8eb2   nginx     "/docker-entrypoint.…"   4 seconds ago    Up 3 seconds    0.0.0.0:3344->80/tcp   nginx01
c3cfcb2c5e28   centos    "/bin/bash"              30 minutes ago   Up 30 minutes                          musing_hopper
[root@VM-0-10-centos /]# docker stop c3cfcb2c5e28
c3cfcb2c5e28
[root@VM-0-10-centos /]# docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
c6119f4d8eb2   nginx     "/docker-entrypoint.…"   46 seconds ago   Up 46 seconds   0.0.0.0:3344->80/tcp   nginx01

# 进入容器

[root@VM-0-10-centos /]# docker exec -it nginx01 /bin/bash
root@c6119f4d8eb2:/# whereis nginx
nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx
root@c6119f4d8eb2:/# cd /etc/nginx
root@c6119f4d8eb2:/etc/nginx# ls
conf.d	fastcgi_params	koi-utf  koi-win  mime.types  modules  nginx.conf  scgi_params	uwsgi_params  win-utf
root@c6119f4d8eb2:/etc/nginx#

```

房贷首付









