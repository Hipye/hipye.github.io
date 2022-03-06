# 为一台路由器编译OpenWrt固件


买了个路由器总喜欢折腾一些从一开始用的别人编译的路由器得固件从潘多拉到OpenWrt用过零零散散得固件总觉得少了点什么 所以一时兴起自己搞起编译固件
首先使用的是win10的wsl内建ubuntu20.04开始编译但总是报错

<!--more-->

## 本地编译

#### 添加依赖
```
sudo apt-get update -y 
sudo apt-get install -y git \
subversion \
g++ \
zlib1g-dev \
build-essential \
python \
python3 \
python3-distutils \
libncurses5-dev \
gawk \
gettext \
unzip \
file \
libssl-dev \
libelf-dev \
ecj \
fastjar \
java-propose-classpath \
build-essential \
libncursesw5-dev \
```

#### clone[[lean]](https://github.com/coolsnowwolf/lede.git)源码
```
git clone https://github.com/coolsnowwolf/lede.git 
```
## 添加第三方软件包

先编辑基础配置文件
**feeds.conf.default** 这个文本类似软件包配置
- [√] kenzo是第三方基础源有想用的软件包
- [√] small是依赖包必须要添加![文件大小](https://camo.githubusercontent.com/010add610fe6bc2bcde0f75677b7eda2909565fc621def657003dbb5f399c695/68747470733a2f2f696d672e736869656c64732e696f2f6769746875622f6c616e6775616765732f636f64652d73697a652f6b656e7a6f6b382f6f70656e7772742d7061636b616765733f636f6c6f723d626c756576696f6c6574)
![IMG_20220307_045025](https://moriz-zoom.coding.net/p/page/d/image/git/raw/master/IMG_20220307_045025.jpg)

```
echo "src-git kenzo https://github.com/kenzok8/openwrt-packages" >> feeds.conf.default
echo "src-git small https://github.com/kenzok8/small" >> feeds.conf.default
```
#### 首次编译
```
./scripts/feeds clean 
./scripts/feeds update -a 
./scripts/feeds  install -a 
make menuconfig 
```

前两项的必须选好 第一项是选择cpu的类别 第二项是你的路由型号
#### dl包
由于国内的网络环境导致在下载所需软件包时会导致失败这里提供一个国内dl镜像
[gitee](https://gitee.com/tolqy/openwrt-lede-dl)

#### 修改默认网关地址
不喜欢路由器的默认地址`192.168.1.1`自己修改
```
vim package/base-files/files/bin/config_generate
```

#### 编译
```
make download -j(nproc) 
make -j(nproc) V=s 
```
编译好的固件在/lede/bin/targets/xxx下

#### 二次编译
```
./scripts/feeds update -a
 ./scripts/feeds install -a
 make defconfig
 make -j(nproc) download
 make -j(nproc) V=s
 ``` 

 第三方编译软件包 [[Lienol/openwrt备份]](https://github.com/OpenWrt-Actions/lienol-openwrt-package)

 官方原版 [[openwrt]](https://github.com/openwrt/openwrt)

 第三方固件地址国内镜像 [[gitee]](https://gitee.com/qmgta/lede)

 利用CI自动构建项目 [[openwrt_Build]](https://github.com/kenzok8/openwrt_Build)

