# 青龙面板安装小记


<!--more-->

#### 切换管理员
```
sudo su -
```

#### 安装 docker-ce
```
curl -fsSL https://get.docker.com | bash -s docker
```
##### 国内加速源
```
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```
##### 国内镜像
```
mkdir -p /etc/docker
cat >/etc/docker/daemon.json << EOF
{
  "registry-mirrors": [
      "http://hub-mirror.c.163.com",
      "https://docker.mirrors.ustc.edu.cn"
  ]
}
EOF
```
#### 创建 docker 工作组   *一般不需要*
groupadd docker

#### 添加用户到 docker 工作组
gpasswd -a ${USER} docker

#### 启动 Docker 并加入开机启动项
`重载配置文件`
systemctl daemon-reload
`开启docker`
systemctl enable docker
`重启docker`
systemctl restart docker

#### 校验 docker
docker version

#### npm模块安装
***question***
<u>Error: Cannot find module 'xxx'</u>

```
docker exec -it qinglong pnpm install crypto-js dotenv got request tough-cookie http-server tunnel ws
```
#### 开始安装青龙面板
##### 拉取镜像
```
docker pull whyour/qinglong:latest
```

##### 启动容器
#####  普通服务器
```
docker run -dit \
  -v $PWD/ql/config:/ql/config \
  -v $PWD/ql/db:/ql/db \
  -v $PWD/ql/log:/ql/log \
  -v $PWD/ql/repo:/ql/repo \
  -v $PWD/ql/raw:/ql/raw \
  -v $PWD/ql/scripts:/ql/scripts \
  -v $PWD/ql/jbot:/ql/jbot \
  -p 5700:5700 \
  -e ENABLE_HANGUP=true \
  -e ENABLE_TG_BOT=true \
  -e ENABLE_WEB_PANEL=true \
  -e TZ=CST-8 \
  --name qinglong \
  --hostname qinglong \
  --restart always \
  whyour/qinglong:latest
```
#####   N1 等路由器
```
docker run -dit \
  -v $PWD/ql/config:/ql/config \
  -v $PWD/ql/db:/ql/db \
  -v $PWD/ql/log:/ql/log \
  -v $PWD/ql/repo:/ql/repo \
  -v $PWD/ql/raw:/ql/raw \
  -v $PWD/ql/scripts:/ql/scripts \
  -v $PWD/ql/jbot:/ql/jbot \
  -e ENABLE_HANGUP=true \
  -e ENABLE_TG_BOT=true \
  -e ENABLE_WEB_PANEL=true \
  -e TZ=CST-8 \
  --net host \
  --name qinglong \
  --hostname qinglong \
  --restart always \
  whyour/qinglong:latest
```
## MacVlan 方式
```
docker run -dit \
  --name qinglong \
  --hostname qinglong \
  --restart always \
  --net=macnet \
  --ip=192.168.2.20 \
  --dns=192.168.2.2 \
  --mac-address C2:F2:9C:C5:B1:01 \
  -v $PWD/ql/config:/ql/config \
  -v $PWD/ql/db:/ql/db \
  -v $PWD/ql/log:/ql/log \
  -v $PWD/ql/repo:/ql/repo \
  -v $PWD/ql/raw:/ql/raw \
  -v $PWD/ql/scripts:/ql/scripts \
  -v $PWD/ql/jbot:/ql/jbot \
  -e ENABLE_HANGUP=true \
  -e ENABLE_TG_BOT=true \
  -e ENABLE_WEB_PANEL=true \
  -e TZ=CST-8 \
  whyour/qinglong:latest
```
#### 修改密码
服务器防火墙放行 5700 端口 (如果是国内云主机，还需要到云服务商安全组 / 外网防火墙处放行 5700 端口)
访问 http://localhost:5700 ，使用 admin/adminadmin 登录，网页会提示已初始化密码，使用以下命令获取新密码
```
docker exec -it qinglong cat /ql/config/auth.json
```
登录面板之后修改用户名和密码即可

#### 脚本拉取
```
# 进入容器
docker exec -it qinglong bash
# 更新青龙
docker exec -it qinglong ql update
# 更新青龙并编译
docker exec -it qinglong ql restart
# 拉取自定义仓库
docker exec -it qinglong ql repo https://github.com/whyour/hundun.git "quanx" "tokens|caiyun|didi|donate|fold|Env"
# 拉取单个脚本
docker exec -it qinglong ql raw https://raw.githubusercontent.com/moposmall/Script/main/Me/jx_cfd.js
# 导出互助码
docker exec -it qinglong ql code
# 删除 7 天前的所有日志
docker exec -it qinglong ql rmlog 7
# 启动 bot
docker exec -it qinglong ql bot
# 通知测试
docker exec -it qinglong notify test test
# 立即执行脚本
docker exec -it qinglong task test.js now
# 并行执行脚本
docker exec -it qinglong task test.js conc
```
