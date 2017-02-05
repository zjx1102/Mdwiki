# Git 常用命令

```java
git init //git目录初始化

git remote add server_ip/registry http://gitserver/xx.git //添加远程仓库地址

git push -u server_ip master //客户端首次提交

git add <file> //提交文件

git add . //提交所有修改的文件

git commit -m "" //提交到本地缓存区

git clean -fd //删除untracked files及目录

git remote set-url server_op/registry http://xxx/xxx.git //修改远程仓库地址

git remote -v //查看所有远程仓库

git remote rm <repository> //删除远程仓库
```