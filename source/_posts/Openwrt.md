---
  title: PVE下的软路由配置
  tag: 软路由
  categirous: 技术
---

PVE是一个虚拟机平台，相对于Windows下的虚拟机来说，PVE是直接建立在硬件上的虚拟机平台。之后在PVE上可以虚拟出各种操作系统。PVE对系统配置要求较低，可以应用在比较老旧的平台上。

感谢BILL MIKE大神，让小白重新认识了路由，以下操作方法均来自BILL Mike 大神。我仅作简单记录，方便自已以后留档查看。

### 软件环境

进行以下操作前需要有一个硬件及软件环境，具体我是参考的BILL MIKE的视频[网盘](https://pan.baidu.com/s/1PobK1yPB-jMbRhOtUX76-Q)。
- 硬件已经安装PVE底层虚拟系统。
- PVE建立好虚拟机。
- 软路由固件
- WinSCP

### PVE平台上的操作

 - WinSCP进入虚拟机后台文件管理目录（SFTP模式）

> PVE的后台地址：安装PVE时候设定的（192.168.2.1）
> 账号：默认root；
> 密码：你自己设定的后台登陆密码
> 其他默认
![](http://pzx8ezizb.bkt.clouddn.com/1.jpg)
- 进入后台的root目录，然后把本地的固件拖到root目录下。**注意**拖拽之前，缩短固件名称（如改成Jump.img）方面后面操作。
- 进入PVE网页管理界面，进入shell，运行如下命令
``` javascript
chmod +x img2kvm
./img2kvm  jump.img(镜像名称） 555（pve虚拟机名称） vm-555-disk-2（转化后名称）
```
![](http://pzx8ezizb.bkt.clouddn.com/11.jpg)

###  虚拟机中的操作

上述步骤，会在指定虚拟机生成一个磁盘。注意观察，刚开始处在未加载状态。
![](http://pzx8ezizb.bkt.clouddn.com/2.jpg)
- 转换完成后进入建立好的虚拟机，可以看到一个新的磁盘disk-1。
- 关闭虚拟机，并把disk-0分离，添加disk-1
- 运行虚拟机，进入控制台，输入如下命令
``` javascript
vi /etc/config/network   修改路由ip地址
passwd   修改路由器登陆密码（默认用户名root）
```
>**Vi编辑器操作方法**
>-i：修改ip，ESC：退出编辑，:wq 保存退出vi
> reboot重启路由后，输入ip地址进入后台管理界面

### 路由器设置

路由器设置前提需要明确路由器充当的定位，此处设置只针对**旁路由**。具体设置见下图

![](http://pzx8ezizb.bkt.clouddn.com/3.jpg)
![](http://pzx8ezizb.bkt.clouddn.com/4.jpg)
![](http://pzx8ezizb.bkt.clouddn.com/5.jpg)

### 最后

攻略简单，以提示自己为主！如有问题欢迎邮件咨询。


