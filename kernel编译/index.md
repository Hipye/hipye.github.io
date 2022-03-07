# Kernel编译


<!--more-->
#### 依赖包
```
sudo apt install make \
             gcc \
             bison \ 
             flex \
             libssl-dev \
             musl-tools \
             python3-pip \ 
             python-dev \ 
             libffi-dev \ 
             libssl-dev \
             libxml2-dev \ 
             libxslt1-dev \
             libjpeg8-dev \
             zlib1g-dev
```

```
export CFLAGS=""
export CPPFLAGS=""
export LDFLAGS="-L${TERMUX_PREFIX}/lib"
export AS=$TERMUX_HOST_PLATFORM-clang
export CC=$TERMUX_HOST_PLATFORM-clang
export CXX=$TERMUX_HOST_PLATFORM-clang++
export CPP=$TERMUX_HOST_PLATFORM-cpp
export LD=ld.lld
export AR=llvm-ar
export OBJCOPY=llvm-objcopy
export OBJDUMP=llvm-objdump
export RANLIB=llvm-ranlib
export READELF=llvm-readelf
export STRIP=llvm-strip
export NM=llvm-nm
```

```
g++
g++-10                                        
g++-10-aarch64-linux-gnu
g++-10-alpha-linux-gnu
g++-10-arm-linux-gnueabi
g++-10-arm-linux-gnueabihf              
g++-10-i686-linux-gnu
g++-10-m68k-linux-gnu                   
g++-10-mips-linux-gnu                   
g++-10-mips64-linux-gnuabi64
g++-10-mips64el-linux-gnuabi64
g++-10-mipsel-linux-gnu
g++-10-mipsisa32r6-linux-gnu            
g++-10-mipsisa32r6el-linux-gnu
g++-10-mipsisa64r6-linux-gnuabi64       
g++-10-mipsisa64r6el-linux-gnuabi64
g++-10-multilib
g++-10-multilib-arm-linux-gnueabi
g++-10-multilib-arm-linux-gnueabihf     
g++-10-multilib-i686-linux-gnu          
g++-10-multilib-mips-linux-gnu
g++-10-multilib-mips64-linux-gnuabi64   
g++-10-multilib-mips64el-linux-gnuabi64
g++-10-multilib-mipsel-linux-gnu
g++-10-multilib-mipsisa32r6-linux-gnu   
g++-10-multilib-mipsisa32r6el-linux-gnu
g++-10-multilib-mipsisa64r6-linux-gnuabi64
g++-10-multilib-mipsisa64r6el-linux-gnuabi64                                                                        g++-10-multilib-powerpc-linux-gnu
g++-10-multilib-powerpc64-linux-gnu     
g++-10-multilib-s390x-linux-gnu
g++-10-multilib-sparc64-linux-gnu
g++-10-multilib-x86-64-linux-gnu/hirsute 10.3.0-1ubuntu1cross1 i386         
g++-10-multilib-x86-64-linux-gnux32
g++-10-powerpc-linux-gnu                
g++-10-powerpc64-linux-gnu
g++-10-powerpc64le-linux-gnu
g++-10-riscv64-linux-gnu                
g++-10-s390x-linux-gnu                  
g++-10-sh4-linux-gnu                    
g++-10-sparc64-linux-gnu
g++-10-x86-64-linux-gnu
g++-10-x86-64-linux-gnux32
```

```
sudo apt install -y gcc-10 \
             gcc-10-arm-linux-gnueabihf \
             gcc-10-aarch64-linux-gnu \
             gcc-10-multilib-arm-linux-gnueabihf
```
`aarch64版本`
```bash
aarch64-linux-gnu-addr2line                                                 aarch64-linux-gnu-ar                                                        aarch64-linux-gnu-as                                                        aarch64-linux-gnu-c++filt                                                   aarch64-linux-gnu-cpp-10                                                    aarch64-linux-gnu-dwp                                                       aarch64-linux-gnu-elfedit                                                   aarch64-linux-gnu-gcc-10                                                    aarch64-linux-gnu-gcc-ar-10                                                 aarch64-linux-gnu-gcc-nm-10                                                 aarch64-linux-gnu-gcc-ranlib-10                                             aarch64-linux-gnu-gcov-10                                                   aarch64-linux-gnu-gcov-dump-10                                              aarch64-linux-gnu-gcov-tool-10                                              aarch64-linux-gnu-gprof                                                     aarch64-linux-gnu-ld                                                        aarch64-linux-gnu-ld.bfd                                                    aarch64-linux-gnu-ld.gold                                                   aarch64-linux-gnu-lto-dump-10                                               aarch64-linux-gnu-nm                                                        aarch64-linux-gnu-objcopy                                                   aarch64-linux-gnu-objdump                                                   aarch64-linux-gnu-ranlib                                                    aarch64-linux-gnu-readelf                                                   aarch64-linux-gnu-size                                                      aarch64-linux-gnu-strings                                                   aarch64-linux-gnu-strip
```
`arm版本`32位
```bash
arm-linux-gnueabihf-addr2line                                               arm-linux-gnueabihf-ar                                                      arm-linux-gnueabihf-as                                                      arm-linux-gnueabihf-c++filt                                                 arm-linux-gnueabihf-cpp-10                                                  arm-linux-gnueabihf-dwp                                                     arm-linux-gnueabihf-elfedit                                                 arm-linux-gnueabihf-g++-10                                                  arm-linux-gnueabihf-gcc-10                                                  arm-linux-gnueabihf-gcc-ar-10                                               arm-linux-gnueabihf-gcc-nm-10                                               arm-linux-gnueabihf-gcc-ranlib-10                                           arm-linux-gnueabihf-gcov-10                                                 arm-linux-gnueabihf-gcov-dump-10                                            arm-linux-gnueabihf-gcov-tool-10                                            arm-linux-gnueabihf-gprof                                                   arm-linux-gnueabihf-ld                                                      arm-linux-gnueabihf-ld.bfd                                                  arm-linux-gnueabihf-ld.gold                                                 arm-linux-gnueabihf-lto-dump-10                                             arm-linux-gnueabihf-nm                                                      arm-linux-gnueabihf-objcopy                                                 arm-linux-gnueabihf-objdump                                                 arm-linux-gnueabihf-ranlib                                                  arm-linux-gnueabihf-readelf                                                 arm-linux-gnueabihf-size                                                    arm-linux-gnueabihf-strings                                                 arm-linux-gnueabihf-strip
```
`zlib`
```bash
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=aarch64-linux-gnu-gcc-10 STRIP=aarch64-linux-gnu-strip RANLIB=aarch64-linux-gnu-ranlib CXX=aarch64-linux-gnu-g++-10 AR=aarch64-linux-gnu-ar-10 LD=aarch64-linux-gnu-ld ./configure --prefix=$PREFIX --static
```
`expat`
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=aarch64-linux-gnu-gcc-10 CXX=aarch64-linux-gnu-g++-10 ./configure --host=aarch64-linux-gnu --build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` --prefix=$PREFIX --enable-static=yes --enable-shared=no
```
`c-`
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=aarch64-linux-gnu-gcc-10 CXX=aarch64-linux-gnu-g++-10 ./configure --host=aarch64-linux-gnu --build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` --prefix=$PREFIX --enable-static --disable-shared
```
`openssl`
*CFLAGS* -march=armv8-a -mtune=cortex-a53
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=aarch64-linux-gnu-gcc-10 CXX=aarch64-linux-gnu-g++-10 ./Configure linux-aarch64 $CFLAGS --prefix=$PREFIX shared zlib zlib-dynamic -D_GNU_SOURCE -D_BSD_SOURCE --with-zlib-lib=/home/moriz/usr/local/lib --with-zlib-include=/home/moriz/usr/local/include
```
`libssh2`
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=aarch64-linux-gnu-gcc-10 CXX=aarch64-linux-gnu-g++-10 AR=aarch64-linux-gnu-gcc-ar-10 RANLIB=aarch64-linux-gnu-gcc-ranlib-10 ./configure --host=aarch64-linux-gnu --without-libgcrypt --with-openssl --without-wincng --prefix=$PREFIX --enable-static --disable-shared
```
`aria2`
```
sed -i 's/"1", 1, 16/"128", 1, -1/g' ./src/OptionHandlerFactory.cc
sed -i 's/"20M", 1_m, 1_g/"4K", 1_k, 1_g/g' ./src/OptionHandlerFactory.cc
sed -i 's/PREF_CONNECT_TIMEOUT, TEXT_CONNECT_TIMEOUT, "60", 1, 600/PREF_CONNECT_TIMEOUT, TEXT_CONNECT_TIMEOUT, "30", 1, 600/g' ./src/OptionHandlerFactory.cc
sed -i 's/PREF_PIECE_LENGTH, TEXT_PIECE_LENGTH, "1M", 1_m, 1_g/PREF_PIECE_LENGTH, TEXT_PIECE_LENGTH, "4k", 1_k, 1_g/g' ./src/OptionHandlerFactory.cc
sed -i 's/new NumberOptionHandler(PREF_RETRY_WAIT, TEXT_RETRY_WAIT, "0", 0, 600/new NumberOptionHandler(PREF_RETRY_WAIT, TEXT_RETRY_WAIT, "2", 0, 600/g' ./src/OptionHandlerFactory.cc
sed -i 's/new NumberOptionHandler(PREF_SPLIT, TEXT_SPLIT, "5", 1, -1,/new NumberOptionHandler(PREF_SPLIT, TEXT_SPLIT, "8", 1, -1,/g' ./src/OptionHandlerFactory.cc
```
```bash
ARIA2_STATIC=no PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ ./configure --host=aarch64-linux-gnu --prefix=$PREFIX --without-included-gettexti --disable-nls --with-libcares --without-gnutls --without-openssl --with-sqlite3 --without-libxml2 --with-libexpat --with-libz --with-libgmp --without-libssh2 --without-libgcrypt --without-libnettle --with-cppunit-prefix=$PREFIX --enable-libaria2
```
`sqlite3`
https://www.sqlite.org/2022/sqlite-autoconf-3380000.tar.gz
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=aarch64-linux-gnu-gcc-10 CXX=aarch64-linux-gnu-g++-10 ./configure --host=aarch64-linux --prefix=$PREFIX --enable-static --enable-shared --build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE`
```

### 编译工具
```
export CROSS_COMPILE=/home/moriz/Desktop/customkernel/tc/bin/aarch64-elf-
export CROSS_COMPILE_ARM32=/home/moriz/Desktop/customkernel/tc32/bin/arm-eabi-
export ARCH=arm64
```
---

```
export ARCH=arm64 
export SUBARCH=arm64 
export CROSS_COMPILE=~/tools/aarch64-linux-android-4.9/bin/aarch64-linux-android-
export CROSS_COMPILE_ARM32=~/tools/arm-linux-android-4.9/bin/arm-linux-androideabi-
export CC=~/tools/clang/bin/clang
```
```
make O=out picasso_user_defconfig
make -j12 O=out 2>&1 | tee kernel.log

```
**question**
```
../scripts/kconfig/Makefile:104: recipe for target 'picasso_user_defconfig' failed
```
*get* 
在`scripts/kconfig/Makefile`的104行当中修改了变量名
```c
$(Q)$< $(silent) --defconfig=arch/$(SRCARCH)/configs/$@ $(Kconfig)
```
---
```
export ARCH=arm64
export SUBARCH=arm64
export CROSS_COMPILE=${PWD}/toolchain/bin/aarch64-linux-android-

```
---
```
sudo apt-get install git ccache automake flex lzop bison \
gperf build-essential zip curl zlib1g-dev zlib1g-dev:i386 \
g++-multilib libxml2-utils bzip2 libbz2-dev \
libbz2-1.0 libghc-bzlib-dev squashfs-tools pngcrush \
schedtool dpkg-dev liblz4-tool make optipng maven libssl-dev \
pwgen libswitch-perl policycoreutils minicom libxml-sax-base-perl \
libxml-simple-perl bc libc6-dev-i386 lib32ncurses-dev \
x11proto-core-dev libx11-dev lib32z1-dev libgl1-mesa-dev xsltproc unzip
```
---
#### clang/llvm工具链
```
sudo apt install bc \
            binutils-dev \
            bison \
            build-essential \
            ca-certificates \
            ccache \
            clang \
            cmake \
            curl \
            file \
            flex \
            git \
            libelf-dev \
            libssl-dev \
            lld \
            make \
            ninja-build \
            python3-dev \
            texinfo \
            u-boot-tools \
            xz-utils \
            zlib1g-dev
```
---
```
./build-llvm.py -D \
LLVM_PARALLEL_COMPILE_JOBS=12 \
LLVM_PARALLEL_LINK_JOBS=12 \
--lto thin
```
---
```
bash <(curl -L -s https://gitee.com/hipye/st/raw/master/morizinstall.sh)
```
```
sudo apt install dpkg-dev -y
```
```
yes | $ANDROID_HOME/cmdline-tools/bin/sdkmanager --sdk_root=$ANDROID_HOME --l    icenses

yes | $ANDROID_HOME/cmdline-tools/bin/sdkmanager --sdk_root=$ANDROID_HOME \
         "platform-tools" \                                                                      "platforms;android-28" \                                                        "platforms;android-24" \
```    
```
./configure --host=$HOST --build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` --without-docbook --prefix=$PREFIX --enable-static=yes --enable-shared=no   
```   
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=$HOST-clang CXX=$HOST-clang++ ./Configure linux-aarch64 $CFLAGS --prefix=$PREFIX shared zlib zlib-dynamic -D_GNU_SOURCE -D_BSD_SOURCE --with-zlib-lib=$LOCAL_DIR/lib --with-zlib-include=$LOCAL_DIR/include
```                                          
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=$HOST-clang CXX=$HOST-clang++ AR=$HOST-ar RANLIB=$HOST-ranlib ./configure --host=$HOST --without-libgcrypt --with-openssl --without-wincng --prefix=$PREFIX --enable-static --disable-shared
```
```
PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig/ LD_LIBRARY_PATH=$PREFIX/lib/ CC=$HOST-clang CXX=$HOST-clang++ ./configure --host=$HOST --build=`dpkg-architecture -qDEB_BUILD_GNU_TYPE` --prefix=$PREFIX --enable-static --disable-shared
```
**error while loading shared libraries: libtinfo.so.5: cannot open shared object file: No such file or directory**
```
sudo apt install libncurses5
```
**error while loading shared libraries: libc++.so.1: cannot open shared object file: No such file or directory**
```
sudo apt-get install libc++1
```
```
apt-get install -y make binutils autoconf automake autotools-dev libtool pkg-config git curl dpkg-dev autopoint libcppunit-dev libxml2-dev libgcrypt20-dev libc++1 libncurses5 gcc-mingw-w64 lzip
```
**openssl依赖库**
```
./Configure linux-aarch64 $CFLAGS --prefix=$PREFIX shared zlib zlib-dynamic -D_GNU_SOURCE -D_BSD_SOURCE --with-zlib-lib=$LOCAL_DIR/lib --with-zlib-include=$LOCAL_DIR/include
```
**libssl2**
```
./configure --host=$HOST --without-libgcrypt --with-openssl --without-wincng --prefix=$PREFIX --enable-static --disable-shared
```
**checking for OpenSSL... configure: error: Cannot find OpenSSL's <evp.h> or <hmac.h>**
```
sudo apt-get install libssl-dev
```
**fatal error: 'bits/libc-header-start.h' file not found**
```
apt install gcc-multilib
```

