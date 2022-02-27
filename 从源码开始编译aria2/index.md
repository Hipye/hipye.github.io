# 从源码开始编译aria2

> aria2编译细节以及error处理
<!--more-->
*使用文档*  
[官方文档(en)](https://aria2.github.io/)
## 编译前注意事项

  1. 根据系统以及平台的不同，编译的方法大同小异。本教程仅提供linux发行版**Kali liunx**的编译方法。
  2. 因为国内的网络你懂的的某些特殊原因，可能在[gayhub](https://www.github.com)上下载作者提供的[源码](https://github.com/aria2/aria2/releases)的时候会出现下载失败以及访问龟速还有 404/`笑而不语`。
  3. 由于不是和我存在同样操作环境下可能会有不同状况发生所以请善用[谷歌](https://www.google.com)`Or`[百度](https://www.baidu.com)

------

## 添加依赖

先更新一下系统的软件

```
sudo apt-get update && apt-get upgrade -y
```

安装编译时官方说明需要的依赖

```
sudo apt-get install -y gcc libgnutls28-dev nettle-dev libssh2-1-dev libc-ares-dev libxml2-dev zlib1g-dev wget perl libsqlite3-dev pkg-config libcppunit-dev autoconf automake autotools-dev autopoint libtool git c++11 g++
```
**2019.04.06新增ubuntu18.10编译条件**
```
sudo apt-get update && sudo apt-get install libgnutls28-dev nettle-dev libgmp-dev libssh2-1-dev libc-ares-dev libxml2-dev zlib1g-dev libsqlite3-dev pkg-config libcppunit-dev autoconf automake autotools-dev autopoint libtool git gcc g++ libxml2-dev make quilt

```

centos指令如下

```
yum install gcc-g++ gcc -y 
```


下载aria2的源码这里我下载的是[1.34](https://github.com/aria2/aria2/archive/release-1.34.0.tar.gz)版本

```
wget https://github.com/aria2/aria2/archive/release-1.34.0.tar.gz
```

