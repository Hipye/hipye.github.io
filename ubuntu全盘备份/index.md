# Ubuntu全盘备份


<!--more-->
dpkg: error processing package xxxxx (--install):
 dependency problems - leaving unconfigured
.....
Errors were encountered while processing:

```
sudo apt --fix-broken install
```
Linux 系统本身的优越性，系统的备份和还原还是比较容易的
`df -lh`

dd 命令直接克隆硬盘分区
```
sudo dd if=/dev/sda1 of=/dev/sdb1
```
还原系统的命令
```
sudo dd if=/dev/sdb1 of=/dev/sda1
```
tar 将硬盘上的文件打包
```
cd /
sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/mnt --exclude=/sys --exclude=/backup.tgz /
```
还原命令
```
tar xvpfz backup.tgz -C /
```

