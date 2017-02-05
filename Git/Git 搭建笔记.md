# Git 搭建笔记
## Git 客户端搭建
### Ubuntu

```
apt-get install git
```

### Centos

```
yum install git
```


## Git 服务端搭建
### 使用gitbucket的docker镜像搭建git服务器
#### 下载镜像和启动容器

```
docker pull 10.3.10.54:9000/gitbucket

docker run -d -p 10000:8080 -p 29418:29418 --restart=always -v /var/gitbucket-data:/gitbucket 10.3.10.54:9000/gitbucket:1.0.0
```
#### 登录和配置git服务器
在浏览器中打开`http://server_ip:10000/`,输入用户名`root`，密码`root`，使用超级管理员登录gitbucket。

在右上角下拉菜单System administration中选择System Setting，进行相关配置。

Base URL中输入：`http://server_ip:10000`

SSH access,选中Enable

#### 使用
退出管理员账号，新建用户账号，并创建仓库。
## Git 使用
### 生成SSH KEY

```
# ssh-keygen -t rsa -C "your_email@example.com"
```

在`~/.ssh/`目录下会有一个`id_rsa.pub`文件

将`id_rsa.pub`添加到git仓库中













