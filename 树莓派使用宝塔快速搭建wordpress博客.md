### 前文

此教程将使用宝塔面板进行wordpress的安装，这也是目前安装wordpress较为简单的方法了。

### 安装系统

如果用官网系统建议使用**Raspbian Buster Lite**，`安装宝塔之后无法使用远程桌面`，如果使用其他系统建议使用64位操作系统这样未来可以升级更高的宝塔版本（Raspbian 全为32位）

<img src="http://liuchengblog.top/wp-content/uploads/2020/04/%E6%89%B9%E6%B3%A8-2020-04-11-230623.png" alt="img"  />





﻿

### 安装宝塔

这里以5.9版本为例（64位系统的也可以安装最新版，不过会有很多bug,下面讲）

**Raspbian/Debian**安装命令：

```
wget -O install.sh http://download.bt.cn/install/install-ubuntu.sh && bash install.sh
```

**Ubuntu/Deepin**安装命令：

```
wget -O install.sh http://download.bt.cn/install/install-ubuntu.sh && sudo bash install.sh
```

注：已知最新版的宝塔在**ubuntu18.04.4/19.10.1**会出现nginx，php扩展redis无法安装,mongo db（5.9也无法启用）安装后无法启用等问题。

### WordPress安装

1.安装对应软件

2.点击网站，点击创建站点来创建一个站点。（数据库和ftp记得创建）

注：如果是内网机可以用树莓派的ip当作域名输入

![img](http://liuchengblog.top/wp-content/uploads/2020/04/%E6%89%B9%E6%B3%A8-2020-04-11-232554-1024x541.png)

3.进入对应文件夹，如上图的**/www/wwwroot/liuchengblog.top**

4.删除里面的所有文件

5.将在wordpress官网的下载的压缩包上传到这里并解压缩，然后把解压得到的文件夹里的文件剪切到**liuchengblog.top**文件夹里。

6.在浏览器输入域名，即可看到**wordpress**设置页

![img](http://liuchengblog.top/wp-content/uploads/2020/04/%E6%89%B9%E6%B3%A8-2020-04-04-221223-1024x638.png)
#### 设置页

```
数据库名，用户名，密码（按创建站点时的数据填写）
数据库主机: localhost 表前缀: wp_
```
![img](http://liuchengblog.top/wp-content/uploads/2020/04/%E6%89%B9%E6%B3%A8-2020-04-04-221329.png)



#### 完成搭建😁

即可根据自己的喜好对博客进行个性化设置了

﻿



> 已知问题
>
> ftp无法使用(反正我是这样)mongo db无法启动