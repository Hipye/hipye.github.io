# 为一台路由器编译OpenWrt固件


买了个路由器总喜欢折腾一些从一开始用的别人编译的路由器得固件从潘多拉到OpenWrt用过零零散散得固件总觉得少了点什么 所以一时兴起自己搞起编译固件
首先使用的是win10的wsl内建ubuntu20.04开始编译但总是报错

<!--more-->
> 买了个路由器总喜欢折腾一些从一开始用的别人编译的路由器得固件从潘多拉到OpenWrt用过零零散散得固件总觉得少了点什么 所以一时兴起自己搞起编译固件
首先使用的是win10的wsl内建ubuntu20.04开始编译但总是报错

## 本地编译

### 添加依赖
```
sudo apt-get update -y 
sudo apt-get install -y git subversion g++ zlib1g-dev build-essential git python python3 python3-distutils libncurses5-dev gawk gettext unzip file libssl-dev wget libelf-dev ecj fastjar java-propose-classpath sudo 
apt-get install build-essential libncursesw5-dev python unzip
```

## clone[lean]源码
```
git clone https://github.com/coolsnowwolf/lede.git 
```
## 添加第三方软件包

既然开整那就弄点不一样的

先编辑基础配置文件<font color="#009DDC">**feeds.conf.default**</font>
```
echo "src-git hipye https://gitee.com/hipye/openwrt-packages" >> feeds.conf.default 
```
## 首次编译
```
./scripts/feeds clean 
./scripts/feeds update -a 
./scripts/feeds install -a 
make menuconfig 
```

前两项的必须选好 第一项是选择cpu的类别 第二项是你的路由型号
### dl包
由于国内的网络环境导致在下载所需软件包时会导致失败这里提供一个国内dl镜像
[gitee](https://gitee.com/tolqy/openwrt-lede-dl)

### 修改默认网关地址
不喜欢路由器的默认地址`192.168.1.1`自己修改
```
cd openwrt
vim package/base-files/files/bin/config_generate
```

### 编译
```
make download -j(nproc) make -j(nproc) V=s 
```
编译好的固件在/lede/bin/targets/xxx下

### 二次编译
```
./scripts/feeds update -a
 ./scripts/feeds install -a
 make defconfig
 make -j8 download
 make -j(nproc) V=s
 ``` 

 第三方编译软件包 Lienol/openwrt
 官方原版地址 openwrt
 第三方固件地址 lede
 利用CI自动构建项目
 esirplayground/AutoBuild-OpenWrt
 Actions-OpenWrt


