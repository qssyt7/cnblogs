WINDOWS 环境下：

# 1. android SDK环境变量。
新建一个文本文件，改名为“adk.bat”文件，写入以下内容：
注意脚本中写你自己本地对应的sdk路径。
```
       @echo 以管理员身份运行，否则会拒绝访问系统变量
         
        setx /M ANDROID_HOME "D:\java\Android_SDK"
         
        setx /M PATH "%%ANDROID_HOME%%\build-tools\29.0.0;%%ANDROID_HOME%%\platform-tools;%%ANDROID_HOME%%\tools;%PATH%;"
         
        pause
```
然后以管理员身份运行BAT文件。
.---------------------------------------------------------------------------------------
# 2. JAVA SDK环境变量。
新建一个文本文件，改名为“jdk.bat”文件，jdk版本1.8。写入以下内容：
注意脚本中写你自己本地对应的sdk路径。
```
        @echo 以管理员身份运行，否则会拒绝访问系统变量
         
       setx /M JAVA_HOME "D:\java\jdk1.8.0_202"
         
        setx /M CLASSPATH ".;%%JAVA_HOME%%\lib;%%JAVA_HOME%%\lib\tools.jar;"
         
        setx /M PATH "%%JAVA_HOME%%\bin;%%JAVA_HOME%%\jre\bin;%PATH%;"
         
        pause
```
然后以管理员身份运行BAT文件。

win7 跑这两个脚本没有问题。执行脚本时，如果杀毒软件报警，请放行。
.---------------------------------------------------------------------------------------
**3. JAVA21 SDK环境变量。**
新建一个文本文件，改名为“jdk21.bat”文件，jdk版本21。写入以下内容：
注意脚本中写你自己本地对应的sdk路径。
```
    @echo 以管理员身份运行，否则会拒绝访问系统变量
     
    setx /M JAVA_HOME "D:\java\jdk-21"
     
    setx /M CLASSPATH ".;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;%JAVA_HOME%\lib;"
     
    setx /M PATH "%JAVA_HOME%\bin;%PATH%;"
     
    pause
```

然后以管理员身份运行BAT文件。

没有测试。只记录一下。做为参考。
.---------------------------------------------------------------------------------------
# 4 Python环境变量：
   新建一个文本文件，改名为“python.bat”文件，写入以下内容：
   注意脚本中写你自己本地对应的PYTHON安装路径。

```
    @echo 以管理员身份运行，否则会拒绝访问系统变量
     
    setx /M PYTHON_HOME "D:\Python\Python310"
          
    setx /M PATH "%%PYTHON_HOME%%;%%PYTHON_HOME%%\Scripts;%PATH%;"
     
    pause
```
然后以管理员身份运行BAT文件。
win11 跑此脚本没有问题，正常通过。

脚本在：
git clone https://gitee.com/qssyt7/script_file.git
完毕。