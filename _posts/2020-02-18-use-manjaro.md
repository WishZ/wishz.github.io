---
title:  "manjaro kde 安装体验小结"
tags: linux manjaro jsdelivr
---

前段时间在公司电脑用windows10 + docker的开发环境，实在是太卡了，发现manjaro这个系统很惊艳，比arch稳定，最终选择了 manjaro kde。
<!--more-->

#### 安装
安装用的U盘安装，使用的是 ultariso。写入硬盘的时候一定要使用RAW的方式去写入，否则会有问题。
注：在家里电脑(Dell 笔记本)安装后，总是黑屏无法进入登录界面，都是显卡驱动导致的，解决办法如下：
1. 进入grub界面后，移动到Manjaro的启动项，按E，在大概倒数第二行，找到 quite 在其后面添加 xdriver=mesa acpi_osi=! acpi_osi="Windows 2009" 按F10就可以顺利进入系统了。
2. 进入系统后修改grub文件。
3. 打开终端，sudo vim /boot/grub/grub.cfg
4. 找到linux /boot/vmlinuz-linux root=UUID=38bd539c-692f-44ea-85d6-2155f06f09fc rw quiet 这一行，大体相同，可能会有点不一样。
5. 在quite后面添加 xdriver=mesa acpi_osi=! acpi_osi="Windows 2009"
6. 重启就OK了。

#### 修改国内源
安装完成后，首先就更改国内源，否则，安装软件非常慢，命令如下
```
sudo pacman-mirrors -i -c China -m rank
```
#### 安装vim
```
sudo pacman -S vim
```
#### 添加arch源
编辑文件` /etc/pacman.conf`,在最后添加如下内容
```
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```
添加之后还要导入`archlinuxcn-keyring` ,在命令行输入如下内容
```
sudo pacman -S archlinuxcn-keyring && sudo pacman -Syy
```
#### 安装ZSH
`raw.github.com`连接失败时可使用国内`cdn`地址,[https://www.jsdelivr.com/](https://www.jsdelivr.com/),例如zsh的cdn地址就是`https://cdn.jsdelivr.net/gh/robbyrussell/oh-my-zsh@master/tools/install.sh`
```
sudo pacman -S zsh //安装zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" //配置oh-my-zsh
chsh -s /bin/zsh //更换默认的shell
```
更改主题
```
sudo vim ~/.zshrc
# 修改ZSH_THEME="steeef"
```
#### 安装输入法
```
sudo pacman -S fcitx-sogoupinyin
sudo pacman -S fcitx-im # 全部安装
sudo pacman -S fcitx-configtool # 图形化配置工具
```
安装完成后，需修改配置 sudo vim ~/.xprofile   在其中加入一下代码
```
export GTK_IM_MODULE=fcitx
export QT_IM_MODULE=fcitx
export XMODIFIERS="@im=fcitx"
```
注：重启电脑后仍无法使用，原因是Arch已经将fcitx-qt4从community[移除](https://www.archlinux.org/packages/community/x86_64/fcitx-qt4/)。 删除fcitx-qt4会导致搜狗拼音无法正常工作，想要恢复的Archer可以通过这个[链接](https://archive.archlinux.org/repos/2019/03/31/community/os/x86_64/fcitx-qt4-4.2.9.6-1-x86_64.pkg.tar.xz)下载最后一个版本。

#### 安装常用软件
archLinux包的[地址](https://aur.archlinux.org/packages/)，可以在里面搜索然后安装,例如安装`sublime-text-3`
```
git clone https://aur.archlinux.org/sublime-text-3-imfix.git
#再执行
bash -c "export SHELL=/bin/bash && makepkg -sir"
```
#### docker 安装
```
sudo pacman -S docker     #docker-compose
sudo systemctl start docker
sudo systemctl enable docker
```