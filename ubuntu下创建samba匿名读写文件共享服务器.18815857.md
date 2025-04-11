# 目的：
局域网内，ubuntu下，创建SAMBA文件共享服务器。匿名读写权限。为了开发项目组文件共享传输方便。
# 环境：
X86_64电脑一台。
# 操作系统：
Ubuntu 20.04 LTS 64位。

# 安装samba
```
$ sudo apt-get install samba
```

# 创建共享目录：
```
# cpsy目录，我这里mount了一个大硬盘。
$ cd /cpsy
$ mkdir samba
$ chmod 777 samba -R
```

# 修改SAMBA配置文件
```
$  sudo  vi /etc/samba/smb.conf

# 最后行加入，以下内容。
[share] 
path=/cpsy/samba/ # 你要共享的目录
public=yes 
writable=yes 
security=share
```
修改您的配置文件时，请将注释内容删除。这里是为了讲的明白。

# smb服务管理：
```
$ sudo systemctl restart smbd
$ sudo systemctl stop smbd
$ sudo systemctl start smbd
```

# windows电脑可以访问共享目录了：
打开资源管理器，在地址栏，输入地址：\\\\ubuntu_IP.
如：\\\\192.168.55.199
读写正常。
![image](https://img2024.cnblogs.com/blog/3273335/202412/3273335-20241217154810726-2071755956.bmp)

# <完毕>