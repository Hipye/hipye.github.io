# Archlinux安装

## 下载ISO文件
[archLinux](https://www.archlinux.org/download/)

## 硬盘分区
分区使用Windows的磁盘管理就行，没必要用DiskGenius
这里我使用的分区方案是 只额外分一个区来挂载 / 目录 EFI利用Windows的EFI分区
不使用swap分区 而是swap文件

## 安装出现不能使用terminal
```
locale-gen en_US.UTF-8
localedef -i en_US -f UTF-8 en_US.UTF-8
export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LCALL=enUS.UTF-8
locale-gen en_US.UTF-8
```

## 安装yay（软件包管理器）

Yay是用GO语言编写的，用于Arch Linux基于CLI的最佳AUR助手，Yay基于yaourt、apacman和pacaur的设计

```
sudo pacman -S git go base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
yay -s arch-wiki-man

## 提升编译速度
Archlinux 提升 makepkg 速度
使用并行编译
在 /etc/makepkg.conf 中找到 MAKEFLAGS，设置为
```
MAKEFLAGS="-j4"
```
数字应改为电脑 CPU 核心数（或线程数）

多线程压缩
安装 pigz 和 pbzip2

```
sudo pacman -S pigz pbzip2
```
修改以下几行
```
COMPRESSXZ=(xz -c -z - --threads=0)
COMPRESSGZ=(pigz -c -f -n)
COMPRESSBZ2=(pbzip2 -c -f)
COMPRESSZST=(zstd -c -z -q - --threads=0)
```

安装 fcitx
```
sudo pacman -S fcitx fcitx-qt5 fcitx-configtool
```
安装 qt4
AUR – qt4 提供了 qt4 安装脚本
```
mkdir -p ~/Software/AUR
cd ~/Software/AUR
git clone https://aur.archlinux.org/qt4.git
cd qt4
makepkg -si
```
安装 qtwebkit
AUR – qtwebkit 提供了 qtwebkit 安装脚本
```
cd ~/Software/AUR
git clone https://aur.archlinux.org/qtwebkit.git
cd qtwebkit
makepkg -si
```
安装 fcitx-qt4
AUR – fcitx-qt4 提供了 fcitx-qt4 安装脚本
```
cd ~/Software/AUR
git clone https://aur.archlinux.org/fcitx-qt4.git
cd fcitx-qt4
makepkg -si
```
安装搜狗拼音输入法
AUR – fcitx-sogoupinyin 提供了 fcitx-sogoupinyin 安装脚本
```
cd ~/Software/AUR
git clone https://aur.archlinux.org/fcitx-sogoupinyin.git
cd fcitx-sogoupinyin
makepkg -si
```
配置 fcitx
修改 ~/.pam_environment 写入

```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```
添加搜狗输入法
在终端中打开 fcitx-configtool

点击 “+” 号，取消勾选 Only show current language，找到 Sogou Pinyin 并添加
参考

## 开启ssh服务

```
sudo pacman -S openssh
sudo systemctl enable sshd
sudo systemctl start sshd
sudo systemctl restart sshd
```
## 更新软件包
使用reflector来获取速度最快的6个镜像，并将地址保存至/etc/pacman.d/mirrorlist
```
reflector -c China -a 6 --sort rate --save /etc/pacman.d/mirrorlist
```

[引用](https://bbs.archlinuxcn.org/viewtopic.php?id=10294)

