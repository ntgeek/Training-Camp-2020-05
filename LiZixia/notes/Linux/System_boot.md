# Linux系统启动

> - 内核引导
> - 运行init
> - 系统初始化
> - 建立终端
> - 用户登录

---

## 内核引导

当BIOS完成自检后，操作系统接管硬件，先读入/boot下的内核文件

## 运行init

init进程是所有进程起点，读取配置`/etc/inittab`

### 运行级别

开机启动。Windows-->服务，Linux-->守护进程

- 运行级别0：系统停机状态。系统默认运行级别不能为0，否则无法正常启动
- 运行级别1：单用户工作状态，root权限，用于系统维护，禁止远程登陆
- 运行级别2：多用户状态（无NFS[^网络文件系统]）
- 运行级别3：完全多用户模式，登录进入控制台命令行模式
- 运行级别4：未使用，保留
- 运行级别5：X11控制台，登陆进入GUI模式
- 运行级别6：系统正常关闭并重启，系统默认运行级别不能为6，否则无法正常启动

## 系统初始化

在init文件中有`si::sysinit:/etc/rc.d/rc.sysinit`，调用执行了/etc/rc.d/rc.sysinit，是每个运行级别都首先要加载的脚本。

主要完成的工作是：激活swap分区，检查磁盘，加载硬件模块等一些需要优先执行的任务

## 建立终端

rc执行结束后返回init，接下来建立终端，共6个(在WSL2的Debian中并没有找到)

> 2345:respawn:/sbin/mingetty tty1
>
> 2345:respawn:/sbin/mingetty tty2
>
> 2345:respawn:/sbin/mingetty tty3
>
> 2345:respawn:/sbin/mingetty tty4
>
> 2345:respawn:/sbin/mingetty tty5
>
> 2345:respawn:/sbin/mingetty tty6

## 用户登录

Linux 的账号验证程序是 login，login 会接收 mingetty 传来的用户名作为用户名参数。

然后 login 会对用户名进行分析：如果用户名不是 root，且存在 /etc/nologin 文件，login 将输出 nologin 文件的内容，然后退出。

这通常用来系统维护时防止非root用户登录。只有/etc/securetty中登记了的终端才允许 root 用户登录，如果不存在这个文件，则 root 用户可以在任何终端上登录。

/etc/usertty文件用于对用户作出附加访问限制，如果不存在这个文件，则没有其他限制。

---

##  关机

``` 
sync #将数据从内存同步到硬盘
shutdown #关机
#参数
-h #时间 "now" "10(min)" "+10" "20:20"
-r #重启，等同于reboot
halt #关闭系统，等同于shutdown -h now poweroff
```

---

2020/5/16