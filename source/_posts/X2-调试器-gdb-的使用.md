title: X2 调试器(gdb)的使用
author: Catty2014
tags:
  - OI
  - gdb
  - 调试
categories: []
date: 2019-07-31 20:18:00
---
# GDB的食用
---




gdb是OI赛事中的调试利器

可以配合各种IDE及编辑器例如Dev-Cpp ~~(虽然Dev-Cpp的调试是个残废)~~ ,CLion,VSCode,Emacs~~OS~~等食用

<font color=aaaaaa>
(Vim下还没有一个与GDB契合完美的插件,所以不算在内。如果有的话,能否安利一下?
</font>

不过这里主要讲的是命令行操作

因为命令行使用范围广泛(雾

而且有图形界面的IDE都可以用gdb命令

# 如何运行

## Sample:ZSH

如图,在命令行内输入"gdb "+程序名就可以调试了

程序名需写全,且编译时要加上`-g`参数

(请自行忽略背景

![eNrT1J.png](https://s2.ax1x.com/2019/07/31/eNrT1J.png)

## VSCode

在配置好调试选项后就可以选择左方工具栏的DEBUG选项调试了

![eNsucj.png](https://s2.ax1x.com/2019/07/31/eNsucj.png)


# 命令简介

<font color=66ccff>\*下列命令均可以简写(如break => b),只要不发生歧义<br>
  \*()中的为可选参数,[]中的为必选参数
</font>

|命令|说明|
|:--|:--|
|list (line)|显示(line)上下5行的源码|
|break [line] |在[line]行设置一个断点|
|info|描述程序的状态|
|run|运行程序|
|display|跟踪变量,每一次停下(如遇到断点或Ctrl-C)时输出变量的值|
|step|执行下一条语句,有函数时跳入函数|
|next|执行下一条语句,有函数时**不**跳入函数|