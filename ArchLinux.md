# ArchLinux

## optimus-manager

* 在终端使用命令切换显卡
* 先运行 prime-offload

```shell
# 切换为英伟达显卡
optimus-manager --switch nvidia
# 切换为intel核显
optimus-manager --switch intel
```

```shell
# 无效
sudo prime-select nvidia # 切换nvidia显卡
sudo prime-select intel  # 切换intel显卡
sudo prime-select query  # 查看当前使用的显卡
```

> journalctl -p 3 -xb 查看系统日志



* glxinfo命令可以查看当前正在使用的显卡。

```shell
# 切换前默认Intel
[rainerosion@rains-arch ~]$ glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 4600 (HSW GT2)
# 切换NVIDIA显卡后
[rainerosion@rains-arch ~]$ glxinfo | grep "OpenGL renderer"
OpenGL renderer string: GeForce GTX 950M/PCIe/SSE2
  
```

* 查看驱动版本信息

```shell
ls /usr/src | grep nvidia
```

* 查看显卡

```shell
lspci -k | grep -A 2 -E "(VGA|3D)"
```

## 切换nvidia驱动后重启无法进入图形界面
> ```markdown
> 按ctrl+alt+f2进入命令行，输入用户名密码进入（建议），输入命令nvidia-smi查看显卡是否运行正常
> 
> 运行nvidia-xconfig生成配置
> 输入lspci | grep -E "VGA|3D"查看你的显卡PCI地址，
> 将类似图中每行最前面的00.02.0转换成PCI:0:2:0，填在下面代码块中BusID那里，我使用的是NVIDIA，按照图中应该为PCI:1:0:0。将下面代码块添加到/etc/X11/xorg.conf文件中（同理，如果你是使用nvidia-xconfig后无法进入图形界面，你可以（删除/etc/X11/xorg.conf来重新进入图形界面）谨慎操作！！！）：
> Section "Module"
>     Load "modesetting"
> EndSection
> 
> Section "Device"
>     Identifier "nvidia"
>     Driver "nvidia"
>     BusID "PCI:1:0:0"
>     Option "AllowEmptyInitialConfiguration"
> EndSection
> 
> 编辑/usr/share/sddm/scripts/Xsetup文件，将下列内容添加到文件中
> xrandr --setprovideroutputsource modesetting NVIDIA-0
> xrandr --auto
> 
> 

## 切换回intel

> sudo vim /etc/optimus-manager/optimus-manager.conf
>
> 修改 startup_mode=integrated  后 重启


## 登录选择位置

> /usr/share/xsessions



## nmcli 连接wifi

> nmcli dev 查看网络设备
>
> nmcli r wifi on 打开wifi
>
> nmcli r wifi off 关闭wifi
>
> nmcli dev wifi 扫描wifi 

> 1. 创建wifi连接
>
> $ nmcli device wifi connect {wifi名} password {密码}
>
> 2. 删除wifi连接
>
> $ nmcli con del {wifi名}
>
> 3. 启用wifi连接
>
> $ nmcli connection up {wifi名}
>
> $ nmcli device con {网卡名}
>
>  	4.查看已有连接
>
> $ nmcli con

* 若报错`Error: Connection activation failed: (7) Secrets were required, but not provided.` 删除连接记录

```shell
$ nmcli c 
NAME                UUID                                  TYPE      DEVICE
eno1                3e755f37-3cff-314d-bb1b-4efebb6ce566  ethernet  eno1
OpenWrt             14ad438b-9b2b-43c6-a3d1-66dd3bb987dc  wifi      --
$ nmcli c delete OpenWrt
Connection 'OpenWrt' (14ad438b-9b2b-43c6-a3d1-66dd3bb987dc) successfully deleted.
$ nmcli device wifi connect "OpenWrt" password 00000000
Device 'wlp58s0' successfully activated with '180a3ce4-ba1f-405a-94f1-684e538a7be9'.
```

## 查看端口

netstat -anp | grep 端口号

lsof  -i: 端口号

ps -ef 查看进程



## patch补丁

>  Reversed (or previously applied) patch detected! Assume -R? [n]

* `-t`：该参数遇到这种情况直接将打过补丁的文件恢复原样，即未打补丁之前的状态
* `-f`：该参数遇到这种情况则继续打补丁，当然一般情况下会报错，毕竟对比不一致了
* `-N`：忽略该文件



## DPI设置

```shell
# ~/.Xresources
# 默认96
Xft.dpi: 192
```



## 调整透明度

> * xprop 点击窗口获取窗口信息 WM_CLASS(STRING) 后的内容
> * vim ~/.config/picom/picom.conf 
> * 在透明度中新加一行更改指定透明度



## 调节音量

alsamixer

> pgup/pgdowm 增减音量
>
> 1~9 调节音量到 10%-90%

## 调节屏幕亮度

```shell
# 手动切换
切换root用户
cd /sys/class/backlight/intel_backlight
echo 0~512 > brightness

sudo pacman -S acpilight
sudo gpasswd video -a 用户名 # 将当前用户添加到video实现免root控制亮度

# 获取当前亮度
xbacklight -get
# 设置亮度
xbacklight -set 70
# 增加亮度
xbacklight -inc 10
# 减少亮度
xbacklight -dec 10

```

## 切换内核

```shell
# 修改 grub 配置不是必须的，下面那个才是必须的。
$ sudo nano /etc/default/grub
# 这三行是将子菜单展开，这样不用点击 advanced 进去了
GRUB_DISABLE_SUBMENU=y
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
# 等待时间我之前设置为 0s 的，0 就不显示了，这里改大一点 3s
GRUB_TIMEOUT=3

# 改完保存退出 -----------------------------------------


# 更新下 grub 的配置文件，让上面的设置生效，这一步是一定要做的。
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
正在生成 grub 配置文件 ...
找到 Linux 镜像：/boot/vmlinuz-linux-lts
找到 initrd 镜像：/boot/amd-ucode.img /boot/initramfs-linux-lts.img
Found fallback initrd image(s) in /boot:  amd-ucode.img initramfs-linux-lts-fallback.img
找到 Linux 镜像：/boot/vmlinuz-linux
找到 initrd 镜像：/boot/amd-ucode.img /boot/initramfs-linux.img
Found fallback initrd image(s) in /boot:  amd-ucode.img initramfs-linux-fallback.img
警告： os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
完成

```

## 系统

- **关机**

```
shutdown -h 0 #<==O秒后关机
shutdown -h now #<==现在关机
shutdown -h 10 #<==10分钟后关机
shutdown -h 23:20 #<==23：20分关机
shutdown -c #<==取消shutdown关机命令
init 0 #<==立马关机（切换运行级别为0，推荐使用）
halt #<==立马关机
poweroff #<==立马关机

```

- **重启**

```
shutdown -r now #<==现在重启
shutdown -r 23:20 & #<==23：20分重启，加&符号代表把该命令转到后台处理
reboot #<==立马重启（推荐使用）
init 6 #<==立马重启（切换运行级别为6，推荐使用）
```

- **注销**

```
logout #<==立马注销
exit #<==立马注销
在SecureCRT软件中，按快捷键：Ctrl + d #<==推荐使用
```

## 切换java版本

```shell
# 查看archlinux-java使用说明
$ archlinux-java --help

# 查看jdk状态
$ archlinux-java status

Available Java environments:
  java-11-openjdk
  java-8-openjdk (default)

# 获取默认jdk
$ archlinux-java get

java-8-openjdk

# 设置默认jdk
$ sudo archlinux-java set java-11-openjdk

# 查看切换后的jdk版本
$ java -version

openjdk version "11.0.13" 2021-10-19
OpenJDK Runtime Environment (build 11.0.13+8)
OpenJDK 64-Bit Server VM (build 11.0.13+8, mixed mode)

```

## crontab脚本

> - -e : 执行文字编辑器来设定时程表，内定的文字编辑器是 VI，如果你想用别的文字编辑器，则请先设定 VISUAL 环境变数来指定使用那个文字编辑器(比如说 setenv VISUAL joe)
> - -r : 删除目前的时程表
> - -l : 列出目前的时程表
>
> ```
> min hour day mon week program
> ```
>
> | 每分钟定时执行一次       | * * * * * |
> | ------------------------ | --------- |
> | 每小时定时执行一次       | 0 * * * * |
> | 每天定时执行一次         | 0 0 * * * |
> | 每周定时执行一次         | 0 0 * * 0 |
> | 每月定时执行一次         | 0 0 1 * * |
> | 每月最后一天定时执行一次 | 0 0 L * * |
> | 每年定时执行一次         | 0 0 1 1 * |

*  要确保有对目标文件的权限
*  命令要使用绝对路径

## Top

```txt
c： 显示完整的命令
d： 更改刷新频率
f： 增加或减少要显示的列(选中的会变成大写并加*号)
F： 选择排序的列
h： 显示帮助画面
H： 显示线程
i： 忽略闲置和僵死进程
k： 通过给予一个PID和一个signal来终止一个进程。（默认signal为15。在安全模式中此命令被屏蔽）
l:  显示平均负载以及启动时间（即显示影藏第一行）
m： 显示内存信息
M： 根据内存资源使用大小进行排序
N： 按PID由高到低排列
o： 改变列显示的顺序
O： 选择排序的列，与F完全相同
P： 根据CPU资源使用大小进行排序
q： 退出top命令
r： 修改进程的nice值(优先级)。优先级默认为10，正值使优先级降低，反之则提高的优先级
s： 设置刷新频率（默认单位为秒，如有小数则换算成ms）。默认值是5s，输入0值则系统将不断刷新
S： 累计模式（把已完成或退出的子进程占用的CPU时间累计到父进程的MITE+ ）
T： 根据进程使用CPU的累积时间排序
t： 显示进程和CPU状态信息（即显示影藏CPU行）
u： 指定用户进程
W： 将当前设置写入~/.toprc文件，下次启动自动调用toprc文件的设置
<： 向前翻页
>： 向后翻页
?： 显示帮助画面
1(数字1)： 显示每个CPU的详细情况


```

## scp

```
#上传本地文件夹到Linux
scp -r -p 22 {本地文件夹} Linux用户名@ip地址:Linux绝对路径
#上传文件
scp -p 22 {本地文件} Linux用户名@ip地址:Linux绝对路径

# 上传
去掉指定端口号参数-p, 并将上述路径舒徐调换即可
```

# tools

## hexo 部署博客

hexo clean 清除缓存

hexo (d)eploy  部署

hexo (g)ene

## docker

### 备份和恢复mysql数据

单数据库

> ```shell
> docker exec -i mysql /bin/bash -c 'mysqldump -uroot -p123456 test' > /home/mysql/backup/emp_`date +\%F`.sql;
> ```

多数据库

> ```shell
> docker exec -i mysql /bin/bash -c 'mysqldump -uroot -p123456 --databases test' > /home/mysql/backup/emp_`date +\%F`.sql;
> ```

全数据库

> ```shell
> docker exec -i mysql /bin/bash -c 'mysqldump -uroot -p123456 --all-databases ' > /home/mysql/backup/emp_`date +\%F`.sql;
> ```

**还原：**

> 1. 进入mysql容器, 并选择数据库
>
> 2. ```shell
>    source /var/backup/emp_2023-01-13.sql
>    ```

### 复制到容器

1.  从本机到容器

> docker cp
>
> $ docker cp new_file.txt 0c57de10362b:/usr/share

1. 从容器到容器

> docker volum 
>
> $ docker volume create volume_one
>
> $ docker volume ls
>
> $ docker run -d -v volume_one:/app nginx:latest
>
> $ docker inspect f2457d3eb8fe
>
> `docker volume` 命令的优点之一是创建与多个容器共享的单个目录。

# pacman

## 强制安装

>pacman -S –overwrite 要覆盖的文件模式**

## 在 Arch Linux 上安装 Debtap

>要安装 Debtap，启动终端并使用 AUR 助手安装它：
>
>```
>yay -S debtap
>sudo tabtap -u
>```
>
>使用 cd 命令进入 DEB 文件的目录并使用 Debtap 开始转换包。
>
>```
>cd ~/Downloads
>debtap yourfile.deb
>```
>
>Debtap 将创建一个“**你的文件.zst**” 文件，您可以使用包管理器轻松安装，在本例中为 pacman。
>
>```
>sudo pacman -U yourfile.zst
>```

## 使用dpkg

>1. 安装dpkg
>2. 使用dpkg安装deb包
>
>```
>yay -S dpkg
>dpkg -i .deb包名
>```
