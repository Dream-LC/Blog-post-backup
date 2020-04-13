### 步骤

1. 首先把U盘插入树莓派，然后查看一下是否有被识别到。
    `sudo fdisk -l`
    其中/dev/mmc表示的是TF卡，而/dev/sda/表示的是我们的第一个连接设备（U盘）

2. 查看了U盘已经正确被识别，现在准备进行挂载。
    新建一个目录
    `sudo mkdir /mnt/usb_flash`
    然后挂载设备
    `sudo mount /dev/sda1 /mnt/usb_flash/`
    
3. 需要拔出U盘的时候，可以这样取消挂载
    `sudo umount /mnt/usb_flash`

    注：注：如果使用下面指令报错，可尝试使用`root账号`
    
  ### 树莓派启用root账号

要想使用root帐号，或者说开启root用户，可使用pi用户登录，执行下面命令（此命令是给root账户设置密码的，当切换到root管理员后，此命令无效）

```undefined
sudo passwd root   
```

用下面命令切换到root管理员

```html
su root
```

在那之后会提示输入密码，输入后即可进入root账号

```
pi@raspberrypi:~ $ su root
Password: 
root@raspberrypi:/home/pi# 
```

