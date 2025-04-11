# 目的
   Ubuntu20.04安装QT开发环境，使用QT安装工具安装QT开发环境。
# 操作环境：
1. 笔记本电脑X86_64平台 。
2. Ubuntu 20.04 LTS 64位。

# 下载QT安装工具。
 QT的安装工具下载连接：[https://download.qt.io/archive/online_installers/](https://download.qt.io/archive/online_installers/)
 当前最新版本为4.6。 下载 qt-unified-linux-x64-4.6.1-online.run 安装工具。操作如下：
 打开终端，使用以下指令。
 linux 指令：
 ```
 ##### 使用root用户
 PC:~$ sudo -s 
 ##### 回到root目录
 PC:~# cd ~
 ##### 下载QT安装工具。
 PC:~# wget https://download.qt.io/archive/online_installers/4.6/qt-unified-linux-x64-4.6.1-online.run
 ```
# 安装QT
安装工具下载过程比较慢。建议使用国内镜像，增加下载速度。这里推荐几个国内知名的 Qt 镜像网站，主要是各个高校的：
中国科学技术大学：https://mirrors.ustc.edu.cn/qtproject/
清华大学：https://mirrors.tuna.tsinghua.edu.cn/qt/
南京大学：https://mirror.nju.edu.cn/qt/

 在终端，执行安装指令。
 ```
 ##### 增加执行权限
PC:~#  chmod 755 qt-unified-linux-x64-4.6.1-online.run
 ##### 执行安装工具
PC:~#: ./qt-unified-linux-x64-4.6.1-online.run --mirror https://mirrors.ustc.edu.cn/qtproject/ 
 ```
弹出安装窗口后，按自己的需求，选择不同选项进行安装。我选择了5.15.2LTS，和QTCREATOR LTS。安装完成后，配置一下环境变量。
# QT环境变量
执行linux 指令：
```
# 修改当前用户的环境变量
PC:~# vi .bashrc
```
在[.bashrc]文件末尾增加以下变量：
```
##### QT的安装根目录。
export QTDIR="/disk_sdb/Qt"
export PATH="$QTDIR/5.15.2/gcc_64/bin:$QTDIR/Tools/QtCreator/bin:$PATH"
export LD_LIBRARY_PATH="$QTDIR/gcc_64/lib:$LD_LIBRARY_PATH"
export QT_PLUGIN_PATH="$QTDIR/gcc_64/plugins:$QT_PLUGIN_PATH"
export QML2_IMPORT_PATH="$QTDIR/gcc_64/qml:$QML2_IMPORT_PATH"
```
编辑完成后，保存退出。
#  打开qtcreator.

 执行linux 指令：
 ```
 PC:~# qtcreator
```
# 备注，
为了解决不同用户的权限问题，全程使用root用户，包括打开qtcreator进行开发。

完毕。
