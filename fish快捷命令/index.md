# Fish快捷命令


<!--more-->
```bash
$fish_complete_path
```
查看fish的默认配置文件夹
```bash
~/.config/fish/
```
在文件夹下添加`config.fish`

检查现有远程连接，如果没有，则显示空
git remote -v

添加远程连接, URL可以是远程repo的http或ssh地址 (先设定为origin)
git remote add origin URL

或者修改现有远程URL (这里先设定为origin)
git remote set-url origin URL

先与远程同步
git pull origin master

提交到远程
git push origin master

将本地新建的分之推到远程（远程也新建相应的分之）
git push -u origin <branch>

删除主分支、推送到远端仓库
git branch -D master
git push origin :master

在自己的开发分支拉一个新分支master，推送远端仓库
git checkout -b master
git push -u origin master
