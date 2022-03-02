# 从源码开始编译aria2

> aria2编译细节以及error处理
<!--more-->
使用文档  
[官方文档(en)](https://aria2.github.io/)
### 编译前注意事项

根据系统以及平台的不同，编译的方法大同小异。本教程仅提供linux发行版[ubuntu]的编译方法。
因为国内的网络你懂的的某些特殊原因，可能在[github](https://www.github.com)上下载作者提供的[源码](https://github.com/aria2/aria2/releases)的时候会出现下载失败以及访问龟速
因为不是和我存在同样操作环境下可能会有不同状况发生所以请善用[google](https://www.google.com)或者[百度](https://www.baidu.com)

------

### 添加依赖

先更新一下系统的软件

```
sudo apt-get update -y && sudo apt-get upgrade -y
```

安装编译时官方说明需要的依赖

```
sudo apt-get install -y gcc libgnutls28-dev nettle-dev libssh2-1-dev libc-ares-dev libxml2-dev zlib1g-dev wget perl libsqlite3-dev pkg-config libcppunit-dev autoconf automake autotools-dev autopoint libtool git c++11 g++
```
2019.04.06新增ubuntu18.10编译条件
```
sudo apt-get install libgnutls28-dev nettle-dev libgmp-dev libssh2-1-dev libc-ares-dev libxml2-dev zlib1g-dev libsqlite3-dev pkg-config libcppunit-dev autoconf automake autotools-dev autopoint libtool git gcc g++ libxml2-dev make quilt

```

centos指令如下

```
yum install gcc-g++ gcc -y 
```
#### 源码下载
下载aria2的源码这里我下载的是[1.36](https://github.com/aria2/aria2/archive/release-1.36.0.tar.gz)版本

```bash
wget https://github.com/aria2/aria2/archive/release-1.36.0.tar.gz
```
源码包里的文件如下
```
.
├── ABOUT-NLS
├── aclocal.m4
├── android-config
├── AUTHORS
├── autom4te.cache
├── ChangeLog
├── compile
├── config.guess
├── config.h
├── config.h.in
├── config.log
├── config.rpath
├── config.status
├── config.sub
├── configure
├── configure.ac
├── COPYING
├── depcomp
├── deps
├── doc
├── Dockerfile.mingw
├── Dockerfile.raspberrypi
├── examples
├── INSTALL
├── install-sh
├── lib
├── libtool
├── LICENSE.OpenSSL
├── ltmain.sh
├── m4
├── Makefile
├── Makefile.am
├── Makefile.in
├── makerelease
├── makerelease-osx.mk
├── mingw-build-memo
├── mingw-config
├── mingw-release
├── missing
├── NEWS
├── osx-package
├── po
├── README
├── README.html
├── README.rst
├── script-helper
├── src
├── stamp-h1
├── test
└── test-driver
```
需要修改的只有`./src`下的文件 没有这个目录则需要执行
```bash
autoreconf -i
```
修改128线程如下
```
sed -i 's/"1", 1, 16/"128", 1, -1/g' ./src/OptionHandlerFactory.cc
sed -i 's/"20M", 1_m, 1_g/"4K", 1_k, 1_g/g' ./src/OptionHandlerFactory.cc
sed -i 's/PREF_CONNECT_TIMEOUT, TEXT_CONNECT_TIMEOUT, "60", 1, 600/PREF_CONNECT_TIMEOUT, TEXT_CONNECT_TIMEOUT, "30", 1, 600/g' ./src/OptionHandlerFactory.cc
sed -i 's/PREF_PIECE_LENGTH, TEXT_PIECE_LENGTH, "1M", 1_m, 1_g/PREF_PIECE_LENGTH, TEXT_PIECE_LENGTH, "4k", 1_k, 1_g/g' ./src/OptionHandlerFactory.cc
sed -i 's/new NumberOptionHandler(PREF_RETRY_WAIT, TEXT_RETRY_WAIT, "0", 0, 600/new NumberOptionHandler(PREF_RETRY_WAIT, TEXT_RETRY_WAIT, "2", 0, 600/g' ./src/OptionHandlerFactory.cc
sed -i 's/new NumberOptionHandler(PREF_SPLIT, TEXT_SPLIT, "5", 1, -1,/new NumberOptionHandler(PREF_SPLIT, TEXT_SPLIT, "8", 1, -1,/g' ./src/OptionHandlerFactory.cc
```

