# Linux添加环境变量

## 第一种方法

直接运行命令

```bash
export PATH=$PATH:/usr/local/webserver/php/bin
```

或者

```bash
export PATH=$PATH:/usr/local/webserver/mysql/bin
```

使用这种方法，只会对当前会话有效，也就是说每当登出或注销系统以后，PATH 设置就会失效，只是临时生效。
  
## 第二种方法

执行`vi ~/.bash_profile`修改文件中PATH一行，将`/usr/local/webserver/php/bin` 和 `/usr/local/webserver/mysql/bin` 加入到`PATH=$PATH:$HOME/bin`一行之后，

```bash
PATH=$PATH:/usr/local/webserver/php/bin:/usr/local/webserver/mysql/bin
export PATH
```

然后运行命令

```bash
source .bash_profile
```

这种方法只对<font color='red'>当前登录</font>用户生效

## 第三种方法

修改`/etc/profile`文件使其永久性生效，并对所有系统用户生效，在文件末尾加上如下两行代码

```bash
PATH=$PATH:/usr/local/webserver/php/bin:/usr/local/webserver/mysql/bin
export PATH
```

最后：执行 命令`source /etc/profile`或执行点命令`./profile`使其修改生效，执行完可通过`echo $PATH`命令查看是否添加成功。