# Os 学习
## Os 系统自带 apache 
路径：`/etc/apache2/`

启动和重启命令：`sudo apachectl start/restart`

## Os启动tree命令

再bash配置中`.bash_profile`添加

`alias tree="find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'"`

然后`source .bash_profile`