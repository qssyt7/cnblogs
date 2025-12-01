# ubuntu_12.04_tftp的安装与设置

## 1.安装 tftp-hpa(这是客户端)   tftpd-hpa(这是服务端)  xinetd(什么是xinetd)

```
sudo apt-get install tftp-hpa tftpd-hpa xinetd
```


# 2.建立服务的目录tftpboot
```
cd ~

mkdir tftpboot

chmod -R 777 tftpboot
```


# 3.修改tftp配置文件，如没有,则创建。
```
sudo vi /etc/xinetd.d/tftp
```
内容：
```
service tftp
{
             disable         = no
             socket_type     = dgram
             protocol        = udp
             wait            = yes
             user            = root
             server          = /usr/sbin/in.tftpd
             server_args     = -s <font color = red> /home/themitec/tftpboot </font>
             source          = 11
             cps             = 100 2
             flags =IPv4
         }
```
# 4.修改tftpd-hpa文件
```
sudo vi /etc/default/tftpd-hpa
```
内容：
```
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="<font color = red>/home/themitec/tftpboot</font>"
TFTP_ADDRESS="0.0.0.0:69"
TFTP_OPTIONS="--secure"  
```     
ubuntu14.04lts64位时， 这个参数改为：`TFTP_OPTIONS="-l -c -s"`，如果是更改这个参数的话，要重启电脑。我这里重启服务不灵。

# 5.测试服务：
进入到`/home/themitec/tftpboot`目录，新建一个文件：
```
vi txt.txt
   :wq
```
查看UDP69端口：
```
netstat -an | more | grep udp
```

服务重启：
```
sudo   /etc/init.d/xinetd  restart 
sudo   /etc/init.d//tftpd-hpa restart
```
连接：
```
   tftp 127.0.0.1
   get txt.txt
```
在windows下tftp get正常。
windows tftp 指令使用请百度“windows 使用tftp”

只测试了get 没有测试put.

# 6.错误处理：
在本地的terminal测试get没有错误。
使用SecureCRT在get时出现错误 tftp: txt.txt: Permission denied，暂时没有解决。

## 说明：
什么是xinetd
xinetd即extended internet daemon，xinetd是新一代的网络守护进程服务程序，又叫超级Internet服务器。经常用来管理多种轻量级Internet服务。xinetd提供类似于inetd+tcp_wrapper的功能，但是更加强大和安全。

the end!