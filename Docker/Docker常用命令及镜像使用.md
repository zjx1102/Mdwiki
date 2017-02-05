# Docker常用命令及镜像使用
## 1. 常用命令
* 开机启动服务

```
chkconfig docker on
service docker start
```
* 查看容器

```
docker ps
```
* 查看所有容器

```
docker ps -a
```
* 停止容器

```
docker stop mybox
```
* 删除容器

```
docker rm mybox
```
* 删除镜像

```
docker rmi myimage
```
## 2. 常用镜像使用
* 私有镜像仓库 `registry:2.4.1`

```
docker pull 10.3.10.54:9000/registry:2.4.1

docker run -d -p 9000:5000 --restart=always --name registry2 -v /opt/resgistry-var/:/var/lib/registry/ registry:2.4.1
```
* 项目管理wiki `camandel/django-wiki`

```
docker pull 10.3.10.54:9000/django-wiki:1.0.0

docker run -d -p 49153:8000 --name django-wiki camandel/django-wiki
```

* 数据库mysql

```
docker pull 10.3.10.54:9000/mysql:1.0.0

docker run -it --name mysqlserver -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql:1.0.0

docker exec -it mysqlserver bash
mysql -uroot -p123456
show databases;
```

* tomcat

```
docker pull 10.3.10.54:9000/tomcat:1.0.0

docker run -d -p 8899:8080 --name tomcatserver tomcat:1.0.0
```

* gitbucket

```
docker pull 10.3.10.54:9000/gitbucket

docker run -d -p 10000:8080 -p 29418:29418 --restart=always -v /var/gitbucket-data:/gitbucket 10.3.10.54:9000/gitbucket:1.0.0
```

管理员登录并进行设置:在浏览器中打开 http://10.3.10.56:10000/,输入用户名: root, 密码: root 选择右上角下拉菜单中的System administration, 选择System Setting,进行相关的设置: Base URL中输入:http://10.3.10.56:10000Account registration,选中AllowSSH access,选中Enable (可选)最后点击Apply changes,保存。选择右上角下拉菜单中的Account setting,选择Profile,可修改密码。

创建新用户gitbucket 密码git

创建仓库

```
Create a new repository on the command line
touch README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin http://10.3.10.56:10000/git/gitbucket/registry.git
git push -u origin master
```

Push an existing repository from the command line

```
git remote add origin http://10.3.10.56:10000/git/gitbucket/registry.git
git push -u origin master
```

* maven

```
docker pull 10.3.10.54:9000/nexus3:1.0.0

docker run -d -p 10001:8081 --restart=always --name nexus3 -v /var/nexus-data:/nexus-data 10.3.10.54:9000/nexus3:1.0.0
```

* jenkins

```
docker pull 10.3.10.54:9000/jenkins:1.0.0

ocker run -d -p 10002:8080 --restart=always --privileged -v /var/run/docker.sock:/var/run/docker.sock 10.3.10.54:9000/jenkins:1.0.0
```

* dokuwiki

```
docker run -d -p 8000:80 --name dokuwiki istepanov/dokuwiki
```









