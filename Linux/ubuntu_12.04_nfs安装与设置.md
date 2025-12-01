# ubuntu_12.04_nfs安装与设置

OS： ubuntu 120.4 64位 LTS

## 1.安装NFS
```
$sudo -s
#apt-get install nfs-kernel-server
```

## 2.建立nfs共享目录
```
#cd ~
#mkdir nfsboot
#chmod -R 777 nfsboot
```

## 3.设置权限

打开`/etc/exports`文件，在末尾加入：
```
  /home/<font color = red>themitec</font>/nfsboot *(rw,sync,no_root_squash)
```
这里的"<font color = red>themitec</font>"是我的本地电脑ubuntu的用户名称。

说明：
nfs允许挂载的目录及权限，在文件`/etc/exports`中进行定义，各字段含义如下：
```
/home/themitec/nfsboot：要共享的目录
\* ：允许所有的网段访问
rw ：读写权限
sync：资料同步写入内在和硬盘
no_root_squash：nfs客户端共享目录使用者权限
```

## 4. 重启服务：
```
#sudo /etc/init.d/portmap restart                  <---重启portmap，
#sudo /etc/init.d/nfs-kernel-server restart        <---重启nfs服务
#showmount -e                                      <---显示共享出的目录
```
注：nfs是一个RPC程序，使用它前，需要映射好端口，通过portmap设定

命令运行如下：
```
themitec@themitec-945GZM-S2:~$ sudo /etc/init.d/portmap restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service portmap restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop portmap ; start portmap. The restart(8) utility is also available.
portmap stop/waiting
portmap start/running, process 5387
themitec@themitec-945GZM-S2:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon
   ...done.
 * Unexporting directories for NFS kernel daemon...
   ...done.
 * Exporting directories for NFS kernel daemon...
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/home/themitec/nfsboot".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

   ...done.
 * Starting NFS kernel daemon
   ...done.
themitec@themitec-945GZM-S2:~$ showmount -e
Export list for themitec-945GZM-S2:
/home/themitec/nfsboot *
```

## 5.测试

现在可以在本机上试一下：
```
#sudo mount -t nfs localhost:/home/themitec/nfsboot /mnt
```
注：localhost为本机linux的IP地址

这样就把共享目录挂到了/mnt目录，取消挂载用：
```
#sudo umount /mnt
```

如果用在嵌入式设备上挂载，要加上参数`-o nolock`
我在开发板上使用的挂载命令：
```
mount -t nfs -o nolock 192.168.1.8:/home/themitec/nfsboot /mnt
```

the end!
