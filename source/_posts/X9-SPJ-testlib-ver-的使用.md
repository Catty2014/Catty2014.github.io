title: X9 SPJ(testlib ver.)的使用
author: Catty2014
date: 2019-08-03 16:16:40
tags:
---
# 如何正确使用SPJ
---
啊当然这里讲的是使用testlib

因为手写的SPJ容易炸锅...

## 下载testlib.h

testlib.h是此处要讲到的SPJ实现的根本所在

其中包含了testlib的完整实现

**对于Windows**,请在[此处](https://github.com/MikeMirzayanov/testlib/blob/master/testlib.h)下载（复制）到gcc的include目录

一般是`%PATH_OF_GCC%/include`

例如:
```
D:\gcc\include
C:\Program Files\Dev-Cpp\MinGW64\include
C:\Program Files\CodeBlocks\MinGW64\include
```
**对于GNU/Linux**,**OS X**:
将其放在/usr/include

**通用方法**:放在SPJ所在目录

注意此时要用
```cpp
#include "testlib.h"
```

## Testlib通用函数/状态/变量等
(Note:部分资料来自[OIWiki](https://oi-wiki.org))

### 通用状态

|结果|状态名|含义|
|:--|:--|:--|
|Accepted|`_ok`|答案正确|
|Wrong Answer|`_wa`|答案错误|
|Presentation error|`_pe`|格式错误[1]|
|Partially Correct|`_pc(score)`|答案部分正确,获得score%的分数|
|Fail|`_fail`|程序内部错误,也可以是其他情况[2]|

\[1]:需要注意的是,大部分OJ并不区分WA和PE

\[2]:也可以表示输入不合法(validator),输出有误或选手输出比答案更优

### 通用对象
|对象|含义|
|:--|:--|
|inf|输入流|
|ouf|输出流|
|ans|答案流|

### 通用函数

非成员函数:

|函数|含义|
|:--|:--|
|`void registerTestlibCmd(int argc,char* argv[])`|注册程序为checker(比较器,即SPJ)|
|`void registerInteraction(int argc,char* argv[])`|注册程序为interactor(交互器)|

