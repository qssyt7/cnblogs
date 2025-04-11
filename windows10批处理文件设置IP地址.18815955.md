**环境：** win10 64位

**问题**
由于开发环境需要，要经常修改本地的电脑的IP，所以搞了一个批处理脚本出来。发布出来分享一下。

**操作**
1.桌面新建文本文件，复制粘贴下边脚本。修改脚本为你需要的参数。保存文件。
2.修改文本文件的后缀名，为批处理文件， 修改文件名后缀为bat即可,如 XXX.txt ==>  XXX.bat.
3.以管理员身份执行XXX.bat批处理文件。 

win10 64位 测试功能正常。

**脚本如下：**

```bash
@echo off
chcp 65001
:start
echo =================请输入 数据选择下一操作
echo =================1：IP地址设置192.168.0.196
echo =================2：IP地址设置192.168.0.199
echo =================3：IP地址设置192.168.1.196
echo =================4：IP地址设置192.168.1.199
echo =================5：自动获取IP
echo =================6：IP地址设置192.168.66.199
echo =================0：结束

set /P var=":"

if %var%==1 goto ip196
if %var%==2 goto ip199
if %var%==3 goto ip1196
if %var%==4 goto ip1199
if %var%==5 goto ipdhcp
if %var%==6 goto ip66199
if %var%==0 goto end

:ip196
cls
echo  设置IP地址....
netsh interface ip set addr "以太网" static 192.168.0.196 255.255.255.0 192.168.0.1 1
echo  设置DNS地址....
netsh interface ip set dns "以太网" static 202.106.0.20 primary validate=no
echo *****设置成功！您的IP已修改为内网ip
goto start

:ip199
cls
echo  设置IP地址....
netsh interface ip set addr "以太网" static 192.168.0.199 255.255.255.0 192.168.0.1 1
echo  设置DNS地址....
netsh interface ip set dns "以太网" static 202.106.0.20 primary validate=no
echo *****设置成功！您的IP已修改为内网ip
goto start

:ip1196
cls
echo  设置IP地址....
netsh interface ip set addr "以太网" static 192.168.1.196 255.255.255.0 192.168.1.1 1
echo  设置DNS地址....
netsh interface ip set dns "以太网" static 202.106.0.20 primary validate=no
echo *****设置成功！您的IP已修改为内网ip
goto start

:ip1199
cls
echo  设置IP地址....
netsh interface ip set addr "以太网" static 192.168.1.199 255.255.255.0 192.168.1.1 1
echo  设置DNS地址....
netsh interface ip set dns "以太网" static 202.106.0.20 primary validate=no
echo *****设置成功！您的IP已修改为内网ip
goto start

:ipdhcp
cls
echo  设置IP地址....
netsh interface ip set addr "以太网" source=dhcp
echo  设置DNS地址....
netsh interface ip set dns "以太网" source=dhcp 
echo *****设置成功！dhcp
goto start

:ip66199
cls
echo  设置IP地址....
netsh interface ip set addr "以太网" static 166.66.66.199 255.255.255.0 166.166.66.1 1
echo  设置DNS地址....
netsh interface ip set dns "以太网" static 202.106.0.20 primary validate=no
echo *****设置成功！您的IP已修改为内网ip
goto start


:end
echo 设置结束了
pause

```
脚本在：
git clone https://gitee.com/qssyt7/script_file.git
完毕。
