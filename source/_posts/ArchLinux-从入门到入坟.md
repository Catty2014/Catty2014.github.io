title: 'ArchLinux:从入门到入坟'
author: Catty2014
date: 2019-07-17 16:31:44
tags:
---
本文适合对Linux略有了解的同学食用

新手村: [Ubuntu](https://www.ubuntu.com) [Deepin](https://www.deepin.org)
 
大佬区: [Gentoo](https://www.gentoo.org)  [LFS](https://www.linuxfromscratch.org/lfs)

# 0x00 安装前的准备

## 1.确定安装设备

Arch(及其它发行版)的安装无非就这几类:

1.~~a~~WSL (不属于本文讨论范围)

2.虚拟机(例如VMWare,Virtual Box,等等)

3.真机,2+系统

4.真机,单系统

5.便携式(如U盘,移动硬盘)

~~6.云玩家~~

根据设备的不同,部分安装步骤会有所不同

## 2.确定目标启动类型

启动类型主要有:BIOS,UEFI

\*nix用户可以通过ls /sys/firmware/efi/efivars查看是否是UEFI启动

如果显示很多内容,则为UEFI

如果显示文件不存在(no such file or directory)则是BIOS启动

windows用户可以用msinfo32查看

## 3.准备安装物品

包含了硬件和软件

硬件:

一台活电脑,什么系统都可以

一个2G以上,USB2.0或更好的U盘
(对于0x00-1中提到的方式,3和4必备,5建议使用,2不需要)

>因为Arch有时会滚挂,这个U盘要常备,所以最好是那种已经不用了的老U盘

>不过不能有坏扇区

>对于真机安装,这个U盘是必须

目标设备(对应):
2 足够的磁盘空间
3 更大的磁盘空间
4 足够的磁盘空间
5 一个32G+(最小8G),USB3.0或更好的U盘或移动硬盘

软件:

dd (\*nix,系统自带)

rufus (Windows)

Archiso (去Arch官网/镜像站下载,版本不限)

