# Linuximagemagick压缩命令

> Linux使用图片压缩命令压缩图片大小

[博客多图页面必备]^(ImageMagick)
<!--more-->
#### 安装
```
sudo apt-get install imagemagick
```
#### 使用说明
```
imagemagick的命令convert可以完成此任务,其参数-resize用来改变图片尺寸,可以直接指定像素值,也可以指定缩放百分比。而如果想降低图片的质量,可以用convert的-quality参数,质量值为0-100之间的数值,数字越大,质量越好,一般指定70-80,基本上看不出前后的差别。
强大的convert命令  convert命令可以用来转换图像的格式，支持JPG, BMP, PCX, GIF, PNG, TIFF, XPM和XWD等类型。
```
#### 详情
```bash
identify IMG_xxx.jpg  
xxx.jpg JPEG 2437x1125 2437x1125+0+0 8-bit sRGB 1.24503MiB 0.000u 0:00.001
```
![IMG_20220303_085754](https://moriz-zoom.coding.net/p/page/d/image/git/raw/master/IMG_20220303_085754.jpg)
```bash
convert  xxx.jpg  xxx.png     将jpeg转成png文件 
convert  xxx.gif   xxx.bmp    将gif转换成bmp图像 
convert  xxx.tiff  xxx.pcx   将tiff转换成pcx图像 
```

```
convert -resize 1024x768  xxx.jpg   xxx1.jpg
```
将图像的像素改为1024*768，注意1024与768之间是小写字母
```
convert -sample 50%x50%  xxx.jpg  xxx1.jpg
```
将图像的缩减为原来的50%*50%
```
convert -rotate 270 xxx.jpg xxx-final.jpg
```
旋转图像   将图像顺时针旋转270度 
```
convert -fill black -pointsize 60 -font helvetica -draw 'text 10,80 "Hello, World!" ‘  hello.jpg  helloworld.jpg
```
使用-draw选项还可以在图像里面添加文字
