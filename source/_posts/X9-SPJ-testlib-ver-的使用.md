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

