# shell脚本：文件+文件夹

> if判断实例
<!--more-->
```
if [ ! -d $变量 ];then
#command
fi
```
|  |  |  |
|:----:|:----:|:----:|
| -e | 判断文件目录| 不可和-f组合|
| -f | 判断文件| 不可和-e组合|
| -r | 检查文件夹或者文件是否可写| 可组合|
| -w | 检查文件夹或者文件是否可写| 可组合|
| -x | 检查文件夹或者文件是否可执行| 可组合|
| -s |  检查文件长度| none|
| -h | 检查文件是否软链接| ln -s生成|
| -L| 检查文件是否符号链接| none|
#### nodejs安装
`curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -`
```
## Run `sudo apt-get install -y nodejs` to install Node.js 14.x and npm
## You may also need development tools to build native addons:
     sudo apt-get install gcc g++ make
## To install the Yarn package manager, run:
     curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
     echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
     sudo apt-get update && sudo apt-get install yarn
```
[Tobe ]^(未完待续)

