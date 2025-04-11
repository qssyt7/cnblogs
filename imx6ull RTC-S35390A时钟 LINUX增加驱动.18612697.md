CPU平台:imx6ull
软件平台：qt+linux4.1.15

# 驱动部分：
在驱动编写中，对S35390A的地址填写为0x30+指令，实际只需要用到0x30、0x31、0x32。 （i2c-imx.c 中发送和接收时，设备地址，有一个左移一位）

1.i2c设备树中增加：
```
rtc: rtc-s35390a@60 {
	compatible = "s35390a";
	reg = <0x30>;
};
```
compatible = "s35390a";设备的名字
reg = <0x30>; s35390a的i2c设备地址

2. make menuconfig 中，选中 s35390a的驱动。


# 应用控制部分：
date 指令 显示当前时间。
ntpdate -u ntp.api.bz 指令 开发板对时。
hwclock -w 指令 向实时时钟写入时间


RTC 对应设备文件：/dev/下的rtc、rtc0、rtc1。

完毕