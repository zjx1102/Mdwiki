# SSH 使用

## SSH 查询服务

`ps -e | grep ssh`

## SSH 安装

### Ubuntu

`apt-get install openssh-server`

### Centos

`yum install openssh-server`

## SSH 启动服务

`server sshd start`

或

`/etc/init.d/ssh start`

## SSH 秘钥

### 本地生成公钥

`ssh-keygen -t rsa` 会有一个`id_rsa.pub`的公钥

### 将公钥放到服务器上

将id_rsa.pub拷贝到服务器的`~/.ssh/`目录下，改名为`authorized_keys`

若`authorized_keys`文件存在，则将`id_rsa.pub`内容添加到`authorized_keys`中。

## SSH 使用pem登录

将`.pem`文件拷贝到本地`~/.ssh/`目录中

使用`ssh -i ~/.ssh/.pem root@server_ip`命令登录