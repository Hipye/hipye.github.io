# Llvm交叉编译


<!--more-->

```
sdkmanager \
"platform-tools" \
"build-tools;28.0.3" \
"platforms;android-33" \
"platforms;android-28" \
"platforms;android-24" \
"platforms;android-21"
```

```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib ./Configure linux-aarch64  -march=armv7-a -mtune=cortex-a9 --prefix=/data/data/com.termux/files/usr shared zlib zlib-dynamic -D_GNU_SOURCE -D_BSD_SOURCE --with-zlib-lib=/data/data/com.termux/files/usr/lib --with-zlib-include=/data/data/com.termux/files/usr/include
```
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ ./configure --host=aarch64-linux-android21 --without-libgcrypt --with-openssl --without-wincng --prefix=/data/data/com.termux/files/usr --enable-static --disable-shared
```
```
./configure \
    --host=aarch64-linux-android21 \
    --build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` \
    --prefix=/data/data/com.termux/files/usr \
    --disable-nls \
    --without-gnutls \
    --with-openssl \
    --without-libxml2 \
    --with-libz --with-libz-prefix=/data/data/com.termux/files/usr \
    --with-libexpat --with-libexpat-prefix=/data/data/com.termux/files/usr \
    --with-slite3 --with-sqlite3-prefix=/data/data/com.termux/files/usr \
    --with-libcares --with-libcares-prefix=/data/data/com.termux/files/usr \
    LDFLAGS="-L/data/data/com.termux/files/usr/lib" \
    PKG_CONFIG_PATH="/data/data/com.termux/files/usr/lib/pkgconfig" \
    LD="aarch64-linux-android-ld" \
    ARIA2_STATIC=yes
```
export LD=/opt/llvm/prebuilt/linux-x86_64/bin/ld
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib export CROSS_COMPILE=armv7a-linux-androideabi- --prefix=/data/data/com.termux/files/usr android
```

CXX=aarch64-linux-android29-clang++ CC=aarch64-linux-android29-clang AR=aarch64-linux-android-ar LD=aarch64-linux-android-ld
 ./Configure android-arm64 -D__ANDROID_API__=21 --prefix=/data/data/com.termux/files/usr
`opssl`

```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./configure --prefix=/data/data/com.termux/files/usr --static
```
`zlib`
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./configure \
--host=aarch64-linux-android \
--prefix=/data/data/com.termux/files/usr \
--build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` \
--enable-static=yes \
--enable-shared=no
```
`expat`
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./configure \
--host=aarch64-linux-android \
--prefix=/data/data/com.termux/files/usr \
--build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` \
--enable-static \
--disable-shared
```
c-are
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./Configure \
android-arm64 -march=armv8-a -mtune=cortex-a53 \
--prefix=/data/data/com.termux/files/usr \
shared zlib zlib-dynamic -D_GNU_SOURCE -D_BSD_SOURCE \
--with-zlib-lib=/data/data/com.termux/files/usr/lib \
--with-zlib-include=/data/data/com.termux/files/usr/include
```
`openssl`
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./configure \
CPPFLAGS="-I,/data/data/com.termux/files/usr/include" \
LDFLAGS="-Wl,-rpath-link,/data/data/com.termux/files/usr/lib" \
--prefix="/data/data/com.termux/files/usr" \
--with-libssl-prefix=/data/data/com.termux/files/usr \
--with-libz-prefix=/data/data/com.termux/files/usr \
--host=aarch64-linux-android
```
`libssh2`
```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./configure --host=aarch64-linux-android \
--prefix=/data/data/com.termux/files/usr/ --enable-static \
--enable-shared \
--build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE`
```
`sql`
在编译 aria2时因为1.36相比1.35有修改所以必须修改到源码部分才能顺利编译
_
**这一步必须↓操作，不然进行ARIA2_STATIC=yes链接会失败**
```
sed -i 's|-lrt||g;s|-lpthread||g' $(grep -rEl '\-lrt|\-lpthread' .)
sed -i 's|timegm(|timegm_(|g' $(grep -rl 'timegm(' .)
```

```
PKG_CONFIG_PATH=/data/data/com.termux/files/usr/lib/pkgconfig/ \
LD_LIBRARY_PATH=/data/data/com.termux/files/usr/lib/ \
CXX=aarch64-linux-android29-clang++ \
CC=aarch64-linux-android29-clang \
AR=aarch64-linux-android-ar \
RANLIB=aarch64-linux-android-ranlib \
./configure \
--host=aarch64-linux-android \
--build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` \
--prefix=/data/data/com.termux/files/usr/ \
--disable-nls \
--without-gnutls \
--with-openssl \
--without-libxml2 \
--with-libz --with-libz-prefix=/data/data/com.termux/files/usr/ \
--with-libexpat --with-libexpat-prefix=/data/data/com.termux/files/usr/ \
--with-slite3 --with-sqlite3-prefix=/data/data/com.termux/files/usr/ \
--with-libcares --with-libcares-prefix=/data/data/com.termux/files/usr/ \
--with-ca-bundle='/etc/ssl/certs/ca-certificates.crt' \
LDFLAGS="-L/data/data/com.termux/files/usr/lib" \
PKG_CONFIG_PATH="/data/data/com.termux/files/usr/lib/pkgconfig" \
ARIA2_STATIC=yes
```
`aria2`

打包`系统自带工具`
```
sudo checkinstall -D --install=no
```
新建文件夹解包
```
pkg-deb -R openssl-1.1.1k_amd64.deb .
```
重新打包`命令不一样`
```
dpkg -b xxx new_deb_name.deb
```
