### 设置一个Apache Web服务器

Apache是一种流行的Web服务器应用程序，您可以将其安装在Raspberry Pi上以使其能够提供网页服务。

Apache本身可以通过HTTP提供HTML文件。通过其他模块，它可以使用脚本语言（例如PHP）为动态网页提供服务。

### 安装Apache

- 通过从菜单中选择**附件** > **终端**来打开终端窗口。

- `apache2`通过在终端中键入以下命令并按来安装软件包

  ```
  sudo apt-get install apache2 -y
  ```

  

### 测试Web服务器

默认情况下，Apache将测试HTML文件放在Web文件夹中，您可以从Pi或网络上的另一台计算机上查看该文件。

在Raspberry Pi上打开Apache默认网页：

- 通过从菜单中选择**Internet** > **Chromium Web Browser**打开Chromium 。

- 输入地址`http://localhost`。

  

### 安装PHP

PHP是**预处理器**：当服务器通过网络浏览器收到网页请求时，它将运行代码。它计算出需要在页面上显示的内容，然后将该页面发送到浏览器。与静态HTML不同，PHP在不同情况下可以显示不同的内容。其他语言也可以做到这一点，但是由于WordPress是用PHP编写的，因此这是我们这次需要使用的。PHP是网络上一种非常流行的语言：Facebook和Wikipedia等大型项目都是用PHP编写的。

- 使用以下命令安装PHP软件包：

  `sudo apt-get install php -y`

  

------

如果你可以按照上面的安装方法，那下面即可以忽略

- ###### 第一步换源

  1.编辑 /etc/apt/sources.list 文件（软件源），参考如下命令：

  `sudo nano /etc/apt/sources.list`

  2.用`#`注释掉原来的内容，然后添加下面内容：
  
  `deb http://mirrors.ustc.edu.cn/raspbian/raspbian/ buster main contrib non-free`
  
  `deb-src http://mirrors.ustc.edu.cn/raspbian/raspbian/ buster main contrib non-free`
  
  3.编辑 /etc/apt/sources.list.d/raspi.list 文件（系统更新源），参考如下命令：
  
  `sudo nano /etc/apt/sources.list.d/raspi.list`
  
  4.同样注释掉原有内容并添加下述内容：
  
  `deb http://mirrors.ustc.edu.cn/archive.raspberrypi.org/debian/ stretch main ui`
  
  5.更新软件源列表
  
  ```
  sudo apt-get update
  ```
  
  

- 安装php

  `sudo apt-get install php -y`

  注：可以用`php -v`来测试安装是否成功

  

### 安装MySQL

MySQL（发音为*My Sequel*或*My SQL*）是一种流行的数据库引擎。与PHP一样，它在Web服务器上也得到广泛使用，这就是WordPress之类的项目使用它的原因，以及为什么这些项目如此受欢迎。

- 尝试使用指令能否直接安装

  1.成功（跳过下面）

  ```bash
  sudo apt-get install php-mysql -y
  ```

​       2.失败（换回官方源再试）
   ```bash
   sudo apt-get install php-mysql -y
   ```

注：官网给的是`sudo apt-get install mysql-server php-mysql -y`可是无法正常安装所以只能分开下载了。

### 安装Mariadb-Server

- 使用指令能否直接安装

  `apt-get install mariadb-server`

- 重新启动Apache：

  ```bash
  sudo service apache2 restart
  ```

### 安装wordpress

- 下载WordPress 。建议直接用迅雷下好，再丢到html目录中去（html目录中不能有其他文件）

指令安装：`sudo wget http://wordpress.org/latest.tar.gz`

- 提取WordPress压缩文件以获取WordPress文件。
  `sudo tar xzf latest.tar.gz`

- 将提取的`wordpress`目录的内容移动到当前目录。

  ```bash
  sudo mv wordpress/* .
  ```

- 通过删除tarball和现在为空的`wordpress`目录来整理。

  ```bash
  sudo rm -rf wordpress latest.tar.gz
  ```

- 将所有这些文件的所有权更改为Apache用户：

  ```bash
  sudo chown -R www-data: 
  ```

###   设置您的WordPress数据库

#### 设置MySQL / MariaDB

要设置WordPress网站，您需要一个数据库。这就是MySQL和MariaDB出现的地方！

- 在终端窗口中运行MySQL安全安装命令。

```bash
sudo mysql_secure_installation
```

- 系统将询问您`Enter current password for root (enter for none):`-按**Enter**。
- 键入**Ÿ**，然后按**Enter键**来`Set root password?`。
- 在`New password:`提示符下**输入**密码，然后按**Enter**。**重要提示：**请记住该root密码，因为以后需要它来设置WordPress。
- 输入**Y**到`Remove anonymous users`。
- 输入**Y**到`Disallow root login remotely`。
- 输入**Y**到`Remove test database and access to it`。
- 输入**Y**到`Reload privilege tables now`。

完成后，您将看到消息`All done!`和`Thanks for using MariaDB!`。

#### 创建WordPress数据库

#### 设置MySQL / MariaDB

要设置WordPress网站，您需要一个数据库。这就是MySQL和MariaDB出现的地方！

- 在终端窗口中运行MySQL安全安装命令。

```bash
sudo mysql_secure_installation
```

- 系统将询问您`Enter current password for root (enter for none):`-按**Enter**。
- 键入**Y**，然后按**Enter键**来`Set root password?`。
- 在`New password:`提示符下**输入**密码，然后按**Enter**。**重要提示：**请记住该root密码，因为以后需要它来设置WordPress。
- 输入**Y**到`Remove anonymous users`。
- 输入**Y**到`Disallow root login remotely`。
- 输入**Y**到`Remove test database and access to it`。
- 输入**Y**到`Reload privilege tables now`。

完成后，您将看到消息`All done!`和`Thanks for using MariaDB!`。

#### 创建WordPress数据库

- `mysql`在终端窗口中运行：

```bash
sudo mysql -uroot -p
```

- 输入您创建的root密码。

消息会打招呼`Welcome to the MariaDB monitor`。

- 在`MariaDB [(none)]>`提示符下使用以下命令为您的WordPress安装创建数据库：

```undefined
create database wordpress;
```

请注意以分号结尾的语句。

如果成功，则应该看到以下内容：

```undefined
Query OK, 1 row affected (0.00 sec)
```

- 现在，将数据库特权授予root用户。**注意：**您需要在后面输入自己的密码`IDENTIFIED BY`。

```undefined
GRANT ALL PRIVILEGES ON wordpress.* TO 'root'@'localhost' IDENTIFIED BY 'YOURPASSWORD';
```

- 为了使更改生效，您将需要刷新数据库特权：

```undefined
FLUSH PRIVILEGES;
```

- 使用Ctrl+ 退出MariaDB提示符D。

  
  
  

### 设置WordPress

## WordPress配置

- 在浏览器输入`http://服务器ip`，您应该会看到一个WordPress页面，点`现在就开始！`。

  <img src="http://liuchengblog.top/wp-content/uploads/2020/04/批注-2020-04-04-221223.png" alt="wordpress2" style="zoom:;" />

- 按如下所示填写基本站点信息：

```undefined
数据库名:      wordpress
用户名:        root
密码:         <YOUR PASSWORD>
数据库主机:     localhost
表前缀:        wp_
```

<img src="http://liuchengblog.top/wp-content/uploads/2020/04/批注-2020-04-04-221329.png" alt="wordpress" style="zoom: 80%;" />



参考资料： 1.https://projects.raspberrypi.org/en/projects/lamp-web-server-with-wordpress/4

