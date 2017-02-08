# Docker企业级镜像仓库Harbor搭建

## 下载

在github上下载harbor安装包：[Habbor安装包](https://github.com/vmware/harbor/releases)

## 配置

下载后完成解压，进入解压包，修改harbor.cfg配置文件，主要修改

```java
//设置域名
hostname = xxxxx
//设置访问协议
ui_url_protocol = http
```

## 安装

运行prepare脚本生成配置文件：

```java
# ./prepare
```

执行docker-compose启动harbor

```java
# docker-compose up -d
```

## 启动和停止

相关命令为：`docker-compose start` 和 `docker-compose stop`

## 使用

修改docker配置文件，增加非安全访问的私有库地址。

**ubuntu**:

路径`/etc/docker/`下修改文件`daemon.json`
添加：

```java
{
	"insecure-registries":["10.3.10.54:9000","10.3.10.54"],
	"registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]
}
```

然后重启docker服务：`service docker restart`

然后后台登录

```java
# docker login 10.3.10.54
```