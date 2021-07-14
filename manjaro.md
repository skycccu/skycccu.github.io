# 系统是最新
```
sudo pacman -Syu
sudo pacman -S --needed base-devel git
```

# 安装AUR助手
```
sudo pacman -S --needed base-devel git
git clone https://aur.archlinux.org/yay-git.git
cd yay
makepkg -si
error:go: github.com/Jguer/aur@v1.0.0: Get "https://proxy.golang.org/github.com/%21jguer/aur/@v/v1.0.0.mod": dial tcp 216.58.200.241:443: i/o timeout
make: *** [Makefile:112：yay] 错误 1
==> 错误： 在 build() 中发生一个错误。
```


# 安装常用软件
```
sudo pacman -S yay vim
sudo pacman -S net-tools aria2 goldendict
yay -S debtap
sudo debtap -u
sudo pacman -S wine-mono
pacman -S deepin-system-monitor
yay -s deepin-wine-wechat  deepin-wine-baidupan deepin.com.thunderspeed
yay -S fcitx-im fcitx-configtool fcitx-googlepinyin fcitx fcitx-gtk2 fcitx-gtk3  fcitx-qt5 fcitx-sogoupinyin
yay -S wps-office-cn wps-office-mui-zh-cn ttf-wps-fonts
yay -S google-chrome
```

# /etc/profile
```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```






# 切换国内pacman源,在弹出的窗口里选择软件源,选择阿里源或者华为源,校园网可以选择清华源或者上海交大源
```
sudo pacman-mirrors -i -c China -m rank
```

# 增加archlinuxcn源,编辑/etc/pacman.conf,增加以下
```
[archlinuxcn]
Server = https://mirrors.aliyun.com/archlinuxcn/$arch
```
# 更新下
sudo pacman -Syy
# 安装 archlinuxcn-keyring 包导入GPG key
sudo pacman -S archlinuxcn-keyring

# notce
```
error:无效或已损坏的软件包
已损坏 (无效或已损坏的软件包 (PGP 签名)).
打算删除吗？ [Y/n] y
错误：无法提交处理 (无效或已损坏的软件包 (PGP 签名))
发生错误，没有软件包被更新。

#解决办法：
rm -fr /etc/pacman.d/gnupg
pacman-key --init
pacman-key --populate archlinux
pacman-key --populate archlinuxcn
```
