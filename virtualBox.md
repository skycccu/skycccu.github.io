# 解决VirtualBox无法安装增强工具（0x80004005）

### 点击「设备」-「安装增强功能」，出现如下类似报错：
```
Unable to insert the virtual optical disk D:\Program\Orade\VirtualBox\VBoxGuestAdditions.iso into the machine lubuntu1810.
Could not mount the media/drive 'D:\Program\Orade\VirtualBox\VBoxGuestAdditions.iso' (VERR_PDM_MEDIA_LOCKED).

Result Code: E_FAIL (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}
Callee: IMachine {5047460a-265d-4538-b23e-ddba5fb84976}

```
### 解决方案（以挂载 /home/share 目录为例）
```
// 先安装所需依赖
yum install -y gcc make perl kernel kernel-devel bzip2

// 创建挂载目录
mkdir -p /home/share

// 挂载
mount -t auto /dev/cdrom /home/share

// 手动安装VBoxGuestAdditions
cd /home/share
sh VBoxLinuxAdditions.run
// 该步骤若出现提示执行 `/sbin/rcvboxadd quicksetup all` 命令则执行
/sbin/rcvboxadd quicksetup all

// 重启
shutdown -r now
```

# [Linux] 解决virtualbox共享文件夹没有访问权限的问题
```
在虚拟机上搭建网站，发现访问不了，配置都是正确的，使用下面的命令追踪发信了痕迹

strace $(pidof 'php-fpm: pool www'|sed 's/\([0-9]*\)/-p \1/g')

报的是权限不对，查看共享目录的权限发现是vboxsf的用户组

[pid 1851] lstat("/var/www/phpProject/laykefu/public/index.php", 0x7ffcb08a6170) = -1 EACCES (Permission denied)
[pid  1851] stat("/var/www/phpProject/laykefu/public", 0x7ffcb08a85b0) = -1 EACCES (Permission denied)

[pid  1851] write(4, "\1\7\0\1\0\26\2\0Primary script unknown\0\0"..., 144) = 144

更改那些目录的权限是改不动的，所以使用这个命令把执行用户加入这个组

usermod -aG vboxsf $(whoami)

usermod -aG vboxsf www

cat /etc/group
```
