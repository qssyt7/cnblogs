# UBUNTU 2018.04 LTS 64位 修改当前用户的名称

### 操作步骤如下：

1. 假设你的帐号AAA ， 打算修改为BBB。
2. 开机进入桌面。
3. 按下ctrl + alt + F1~F7 三个组合键。功能键F1到F7任选1个。 进入黑屏。
4. 登陆root 用户，进入后。修改以下三个文件 /etc/passwd， /etc/shadow， /etc/group。
5. 指令`vi /etc/passwd`,找到代表你的那一行，修改用户名AAA为新的用户名BBB。修改完，保存，退出。注意：注意家目录！
6. 指令`vi /etc/shadow`，找到代表你的那一行，修改用户名AAA为新用户名BBB。修改完，保存，退出。
7. 指令`vi /etc/group`，你应该发现你的用户名在很多个组中，全部AAA修改为BBB。修改完，保存，退出。
8. 修改家目录，命令如下:

```bash
cd /home
mv AAA/ BBB/
```

9. 修改完成。使用`reboot`指令重启。
### 完毕。
