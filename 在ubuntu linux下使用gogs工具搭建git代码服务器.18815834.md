# 目标
在ubuntu linux下使用gogs工具，搭建git代码服务器。 搭建私有的github。搭建私有的gitee。

# 环境：
1. ubuntu 1804 LTS 64位。
2. [gogs下载页面](https://gogs.io/docs/installation/install_from_binary)。

# 操作过程：
###  1. 下载gogs. 选择Linux系统amd64平台的zip.
```bash
    $ cd ~
    $ wget  https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_amd64.zip
```
###  2. 解压下载的压缩包。
```bash
    $ unzip -x gogs_0.13.0_linux_amd64.zip
```
解压后的目录：/home/git/gogs
###  3. 到解压目录下, 执行：
```bash
    $ cd gogs 
    $ ./gogs web
```
###  4. 安装配置gogs。
   浏览器访问：http://localhost:3000/install。 远程ssh的话，将localhost换成UBUNTN linux的IP地址。
   在打开的页面，选好参数，安装即可。我们这里小团队人少，选用的sqlite3做为gogs的数据库。
 
###  5. gogs 服务安装一下。
复制gogs.service文件之前先确认一下文件内容的参数是否正确。复制步骤如下：
```bash
    $ cd ~/gogs/scripts/systemd
    $ sudo cp gogs.service /etc/systemd/system/
```
###  6. 使能服务。
大家都在用systemd了，使用比较方便。
```bash
    $ sudo systemctl enable gogs
```
###  7 打开关闭gogs服务。
使用systemd控制gogs服务的打开关闭，就不再使用`./gogs web`指令了。
```bash
    $ sudo systemctl start gogs
    $ sudo systemctl stop gogs
```
### 8.git代码服务器创建完成。
再次访问 http://localhost:3000这个地址, 私有的git服务器就可以使用了。
如果报错，提示有些ubuntu系统依赖包需要安装。自行安装即可。
### 完毕。
