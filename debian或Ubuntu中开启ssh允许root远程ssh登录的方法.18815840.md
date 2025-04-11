debian或Ubuntu中开启ssh允许root远程ssh登录的方法

# 前因：
因开发需要，需要设置开发板的ssh远程连接。

# 操作步骤如下：

1. 安装openssh-server

```
sudo apt install openssh-server
```


2. 设置root用户密码：

```
sudo passwd root
```

3. 允许root用户登录；编辑配置文件：
```
sudo vi /etc/ssh/sshd_config
```

找到此行进行修改，修改前：
```
#PermitRootLogin prohibit-password
```

修改后：
```
PermitRootLogin yes
```

4. 重启ssh服务：
```
sudo systemctl restart sshd
```

修改完成。
电脑端远程工具（putty）连接即可。

结束。

参考：https://cloud.tencent.com/developer/article/1445519
