# 00-引用 介绍
:::info
命令大全：
[https://www.runoob.com/docker/docker-run-command.html](https://www.runoob.com/docker/docker-run-command.html)
狂神学习：
[https://www.bilibili.com/video/BV1og4y1q7M4?p=9&spm_id_from=pageDriver](https://www.bilibili.com/video/BV1og4y1q7M4?p=9&spm_id_from=pageDriver)
博客园[https://www.cnblogs.com/koktlzz/p/14105026.html#%E8%AF%BE%E7%A8%8B%E9%93%BE%E6%8E%A5](https://www.cnblogs.com/koktlzz/p/14105026.html#%E8%AF%BE%E7%A8%8B%E9%93%BE%E6%8E%A5)
csdn：有网络 集群相关的
[https://blog.csdn.net/qq_21197507/article/details/115071715](https://blog.csdn.net/qq_21197507/article/details/115071715)
docker-hub官网：搜索镜像
[https://hub.docker.com/](https://hub.docker.com/)
:::
Docker 原理：
:::info
1，运行原理
在系统中有docker守护进程在一直运行
2，docker为什么比VM快
docker利用的是宿主机的内核，VM则额外需要Guest OS（硬件/系统内核）
:::
**镜像(image)：**
:::info
docker镜像好比一个模板，可以通过这个模板来创建容器(container)，一个镜像可以创建多个容器，类似Python中的Class
:::
**容器(container)：**
:::info
类似Python中通过Class创建的实例，Object；容器可以理解为一个简易的系统
:::
**仓库(repository)：**
:::info
存放镜像的地方
:::
**镜像原理：**
:::info
1，镜像加载原理：
镜像的文件系统是UnionFS（联合文件系统：是分层，轻量级文件系统，所以镜像可以通过分层进行继承）
bootfs：linux启动时会加载bootfs。bootfs是镜像的最顶层，不同rootfs可以共有的同一bootfs。
rootfs：操作系统版本（ubuntu，centos等）。在bootfs之上，包含标准目录：/dev,/proc,/bin等
在之上是应用的image。
bootfs不需要再启动，所以镜像启动很快。
2，系统分层
容器层：可写的，属于UnionFS最上层。
镜像层：是可读，不可写的。
容器启动时，会加载容器层，容器层之下是镜像层。
3，commit镜像
docker commit -m "描述" -a “作者” 容器id 目标镜像名：[TAG]
docker commit -a="xiaofan" -m="add webapps app" d798a5946c1f tomcat007:1.0
:::
## 01-常用命令：
对应的版本在docker文档中：	[https://hub.docker.com/_/mysql?tab=description](https://hub.docker.com/_/mysql?tab=description)
**关于镜像：**
```python
docker images       查看镜像
docker search mysql 搜索镜像
docker pull mysql   拉取镜像
docker pull mysql；5.7 指定版本（版本要在dockerhub中存在）
docker rmi -f 镜像id或者repo名 删除镜像
docker rmi -f $(docker images -aq)删除全部镜像
```
**关于容器**
```python
1，run镜像（会使用pull）
docker run [可选参数] image,
# 参数说明
--name=“Name”   容器名字    tomcat01    tomcat02    用来区分容器
-d      后台方式运行
-it     使用交互方式运行，会进入容器内部
-p      指定容器的端口     -p 8080:8080
    -p  ip:主机端口：容器端口
    -p  主机端口：容器端口（常用）
    -p  容器端口
    容器端口
docker run -it images /bin/bash   每run一次都会创建一次容器，/bin/bash会进入容器
eg：
docker run -it mysql /bin/bash
docker run -it mysql:5.7 /bin/bash
docker run --name redis3 -p 6379:6379 -d redis （常用）后台启动，不使用交互式
(-p 宿主在前：容器在后)

2,进入容器
docker exec -it 容器别名或容器id /bin/bash

3，查看容器
docker ps    # 查看正在运行的容器
docker ps -a  # 查看曾经运行的容器(查看所有容器）
docker ps -aq  # 只显示容器的编号

4，退出容器
exit # 容器停止退出
Ctrl + P + Q # 容器不停止退出 注意必须在英文输入法下，中文输入法不行

5，删除容器
docker rm 容器id         # 删除指定容器 不能删除正在运行的容器
docker rm -f           如果强制删除 rm -f
docker rm -f $(docker ps -aq)     # 删除所有容器
docker rm $(docker ps -aq)
docker ps -a -q|xargs docker rm   # 删除所有容器

6，停止和再启动容器
docker start   容器ID或容器名
docker restart 容器ID或容器名
docker stop    容器ID或容器名
docker kill    容器ID或容器名

7，查看日志
docker logs
docker logs -f -t --tail n 【id】

8，拷贝容器文件：
docker cp 容器id:原地址文件  新地址
eg：
[root@192 home]# docker cp 0569081aa89c:/home/test.java /home

筛选条件删除指令：
##杀死所有容器
docker kill $(docker ps | grep -v CONTAINER | awk '{print $1}')
docker rm $(docker ps -a | grep -v CONTAINER | awk '{print $1}')
##删除已退出的容器
docker rm $(docker ps -a | grep -v CONTAINER |grep Exited | awk '{print $1}')
选出第三列，第五列中没有hour的行；之后只显示当前第三列（现在的第一列）
docker images | grep -v REPOSITORY | awk '{print $3" " $5}'| grep -v hour | awk '{print $1}'
docker rmi -f $(docker images | grep -v REPOSITORY | awk '{print $3" " $5}'| grep -v hour | awk '{print $1}')
##删除所有镜像

##此命令遇到无标签镜像会报错
docker rmi $(docker images | grep -v TAG | awk '{print $1":"$2}')
##删除有标签的镜像
docker rmi $(docker images | grep -v TAG |grep -v none| awk '{print $1":"$2}')
##删除过期镜像(无标签的)
docker rmi -f $(docker images |grep none |awk '{print $3}')
##进入docker
docker attach "CONTAINER ID"
##进入docker执行命令(开启交互式终端)
docker exec "CONTAINER ID" -it /bin/bash

```
**常用数据库操作：**
**Redis**
```python
# docker search redis
# 或者在dockerhub上搜索redis选择拉取指定镜像
docker pull redis 
# docker run --name <容器别名> -p 6379:6379 <镜像名:版本> 
后面可以加 密码：--requirepass 123456
# 前面是宿主机端口，后面是容器端口
docker run -d --name my-redis -p 6379:6379 redis:latest 
# 这样 my-redis容器就跑起来了, -d表示后台运行

进入redis容器：
docker exec -it id/别名 /bin/bash
进入redis界面
docker exec -it id/别名 redis-cli
auth "yourpassword"

创建|修改密码
# 进入容器内部
$ docker exec -it <container id> bash
# 进入redis环境目录
$ cd /usr/local/bin
# 运行redis
$ redis-cli
# 查看当前密码
config get requirepass
# 设置新密码
config set requirepass <new password>

```
**MySQL**
```python
docker search mysql
docker pull mysql
docker run -itd 
    --name local-mysql 
    -p 3306:3306 
    -e MYSQL_ROOT_PASSWORD=a123456 mysql

进入容器中：
docker exec -it mysql bash
进入后查看和启动mysql服务：
service mysql status
service mysql start
```
**Mongo**
 
```python
$ docker pull mongo:latest

# --auth：需要密码才能访问容器服务
$ docker run -itd --name mongo -p 27017:27017 mongo --auth

$ docker exec -it mongo mongo admin
# 创建一个名为 admin，密码为 a123456 的用户。
>  db.createUser({ user:'admin',pwd:'a123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'},"readWriteAnyDatabase"]});
# 尝试使用上面创建的用户信息进行连接。
> db.auth('admin', 'a123456')
```
**容器数据卷：**
```python
数据卷（volume）：host中被挂载的目录

1，挂载（将容器的目录挂载到主机目录，目录形成映射，可以实现同步数据）
使用数据卷：
docker run -it -v /home/ceshi:/home centos /bin/bash
-v 主机目录:容器目录

2，匿名和具名挂载
匿名：-v 后只有容器目录  默认主机目录为：/var/lib/docker/volumes
docker run -d -P --name nginx01 -v /etc/nginx nginx     # -P 随机指定端口
具名：-v 后主机:容器

3，查看所有数据卷（volume）：
docker volume ls
```
### DockerFile
#### 命令
```python
FROM # 基础镜像 比如centos
MAINTAINER # 镜像是谁写的 姓名+邮箱
RUN # 镜像构建时需要运行的命令
ADD # 添加，比如添加一个tomcat压缩包
WORKDIR # 镜像的工作目录
VOLUME # 挂载的目录
EXPOSE # 指定暴露端口，跟-p一个道理
RUN # 最终要运行的
CMD # 指定这个容器启动的时候要运行的命令，只有最后一个会生效，而且可被替代
ENTRYPOINT # 指定这个容器启动的时候要运行的命令，可以追加命令
ONBUILD # 当构建一个被继承Dockerfile 这个时候运行ONBUILD指定，触发指令
COPY # 将文件拷贝到镜像中
ENV # 构建的时候设置环境变量
```
#### 步骤
```python
1，构建文件
vim blog_dockerfile 
文件中加入命令 
~~~shell
FROM java:8
MAINTAINER apple <1446727937@qq.com>
ADD ./blog_api.jar /app.jar
CMD java -jar /app.jar --spring.profiles.active=prod
~~~

2，先把blog_api.jar 放进当前文件夹中

3，再执行构建命令：,
~~~shell
docker build -f ./blog_dockerfile -t app .
~~~
```
### Docker Compose
#### 步骤
```python
# 国内地址
 curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.5/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose 
# 设置文件可执行权限 
 chmod +x /usr/local/bin/docker-compose 
# 查看版本信息 
 docker-compose -version 
```
#### 编写 docker-compose.yml 文件
```python
   version: '3'
   services:
     nginx:
      image: nginx
      container_name: nginx
      ports:
       - 80:80
       - 443:443
      links:
         - app
      depends_on:
       - app
      volumes:
       - /mnt/docker/docker-compose/nginx/:/etc/nginx/
       - /mnt/apple/web:/apple/web   //前者是服务其中的路径，后者为项目中的路径
       - /mnt/apple/blog:/apple/blog
      network_mode: "bridge"
     app:
       image: app
       container_name: app
       expose:
         - "8082"
       network_mode: "bridge"
```
   
