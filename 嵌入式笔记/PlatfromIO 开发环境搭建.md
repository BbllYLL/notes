# 1.下载离线安装包
https://www.yuque.com/attachments/yuque/0/2025/zip/2699676/1756651272420-9df3283a-7acb-4e13-bc99-7c95856ce010.zip?from=https%3A%2F%2Fwww.yuque.com%2Fwelinklab%2Fwwhqxv%2Fwrcmc2edng83gnde

# 2.先检查系统中是否有python可用

![Pasted_20260420175234_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420175234_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

# 3.安装python

双击打开压缩包中的`python-3.13.3-amd64.exe`文件，按下图所示勾选相关选项，点击`Install Now`快速安装
![Pasted_20260420175328_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420175328_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

# 4.更改下载源

打开`cmd`执行如下指令，更新python下载源为国内阿里云源，以提后后续相关软件包下载速度
``` PowerShell
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/
```
执行完毕之后，可以通过如下指令检查执行结果
``` PowerShell
pip config set global.index-url https://mirrors.aliyun.com/pypi/simple/
```
如果显示如下内容，表示更改下载源成功
![Pasted_20260420175444_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420175444_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

# 5.安装Platformio Core

打开`cmd`命令行终端，运行如下指令安装platformio core
```PowerShell
python C:\Users\Admin\Desktop\开发环境相关软件包\get-platformio.py
```

其中的`C:\Users\Admin\Desktop\开发环境相关软件包\get-platformio.py`为压缩包中的文件，请换成自己的文件的路径和使用绝对路径，如下图所示
![Pasted_20260420175645_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420175645_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

安装完成提示如下
![Pasted_20260420175702_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420175702_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

其中绿色文字提示了platformio安装目录

安装完成后，将压缩包中的`开发板离线数据包.zip`这个压缩文件进行解压，得到如下两个文件夹
![Pasted_20260420180228_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420180228_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

将这两个文件夹内容全选复制，然后全部拷贝到上面`platformio core`的安装目录
![Pasted_20260420180245_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420180245_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

# 6.VSCode安装platformio插件
![Pasted_20260420180359_PlatfromIO 开发环境搭建](PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA_assets/Pasted_20260420180359_PlatfromIO%20%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA.png)

