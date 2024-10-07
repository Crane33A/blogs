---
title: Chapter 0.2 初见Python：解释语言，解释器
date: 2024-10-07 10:15:00 +0800
last_modified_at: 2024-10-07 10:30:00 +0800
tags:
  - 计算机科学
  - python
  - 教程
author: sunjhbill
categories:
  - 计算机科学
  - 教程
description: Python解释器、开发环境的安装
---

# Chapter 0.2 初见Python：解释语言，解释器

## Section 1 解释语言——你说得对，但是计算机组成原理，启动！

`Python`是一种**解释性语言**。计算机是这样的，没办法，老是动不动就深入**冯诺依曼**和**图灵**的那个年代去，这里又涉及到一堆对初学者来说**完全没必要了解**的概念：

> 接下来的内容可能会**有些晦涩**，但是还是建议**完整地看下来**，如果想跳过，也请务必**不要跳过**解释性语言的部分。
{: .prompt-warning}

### 编译性语言（静态语言）

~~任何~~编译性语言都会由系统**编译**成**汇编语言**（取决于编译策略，有可能**直接生成**可执行文件），再**汇编**成**机器语言**，也就是计算机可以**直接识别并运行**的0和1。这个过程有可能会通过优化生成的**中间汇编语言文件**来提高运行速度。编译不是**随时进行**的，一次编译生成**当前源代码**对应的可执行文件。

高级语言：

```cpp
#include<iostream>
using namespace std;
int main(){
  int a,res;
  res=0;
  a=10;
  for(i=1;i<=a;i++){
    res+=i;
  }
  cout<<res;
  return 0;
}
```

对应的汇编语言：

```nasm
assume cs: code
code segment
  mov cx,10
  mov ax,0
lp:add ax,cx
  loop lp
code ends
end
```


>汇编语言的语法和处理器的指令集有关，大多数处理器都是`x86`(英特尔酷睿、AMD锐龙)或者`ARM`(苹果M、高通骁龙XElite)指令集，除非你在用龙芯中科的处理器看这篇文章，它是`LoongArch`。但总的来说，`ARM`这个词已经**泛化**了，尤其是高通**自研架构和内核**的情况下，只要不是华为这种被迫或自愿**和国际市场断开联系**的，一般称为`ARM`都无所谓。
{: .prompt-tip}

### 解释性语言（动态语言）
 
 解释性语言在运行的时候实际上是每一行**单独立刻**完成了编译加汇编的过程并立刻运行。由于缺少了**整体性优化**，解释性语言在**性能**上劣于编译性语言，但是也带来了一个额外的bonus：`Python`的开发环境默认带一个**解释器**，可以输入**单行代码**，回车，立刻执行，有利于**调试**。

## Section 2 Python下载——受不了了，直接启动！

无论任何平台，其实都可在[python.org](https://python.org)下载。考虑到在用Linux的人大概率**不需要看**这个教程，这里就不提它了。

> 本教程的重点不在安装，可以参考[CSDN上的“超详细的Python安装和环境搭建教程”](https://blog.csdn.net/qq_53280175/article/details/121107748)
{: .prompt-info}

当前版本，无论是Windows还是macOS，`Python`的安装其实都已经**相当弱智**了，尤其是macOS这边，在`.dmg`磁盘映像文件**满天飞**的情况下使用的是`.pkg`安装包，一路下一步就行。

首先给那些想追随最新版的人：

![](https://pic.imgdb.cn/item/670332f2d29ded1a8cc6b6e5.png)
_Python官网_

进入Python官网并向下滚动，在第二栏**Download**中下方的**Latest**旁边，就是最新版的链接。进入这一链接后，就可以选择**你要使用的版本**了。

![](https://pic.imgdb.cn/item/670332acd29ded1a8cc689de.png)
_下载界面_
### Windows下载安装

Windows所需的版本是Windows installer **64-bit、32-bit或者ARM64**。选择**64位还是32位**取决于你的操作系统，较新的机器**都应选择64位**。ARM64是为**Win on ARM**准备的，如果你的处理器是**高通骁龙**或者该系统是运行在**苹果M芯片上的**虚拟机，建议下载这个版本。

下载好的文件直接打开，勾选下方的**Add Python to PATH**，点击上方的**Install Now**，一路**下一步**即可。最后的完成安装界面上记得点击**Disable Path Length Limit**。

完成后，在你的开始界面-全部应用中应该出现**Python IDLE**(Windows 7/10/11，沟槽的Windows 8改得太厉害了，在搜索界面手动搜添加到磁贴里吧)。
### macOS下载安装

macOS由于没有Windows那么多的**历史包袱**，安装器反而**更简单**，直接双击`.pkg`安装包，一路**下一步**即可。

完成后，在你的启动台中应该出现一个`Python`文件夹，内含一个`IDLE`。
## Section 3 Hello World!——又一次？

打开`IDLE`。这可不是**闲适**的意思，它是**Integrated DeveLopment Environment**的缩写。其他的语言也有**IDE**（缩写中没包含L，实际上是一个东西），但是`Python`有**官方的**IDE，这一点还是**比较少见的**。

![](https://pic.imgdb.cn/item/6703391cd29ded1a8ccb64fa.png)
_Python IDLE_

在这里，你可以直接输入单行的代码执行。接下来我们所有的代码块若含有`>>>`都认为是在IDLE中直接输入的。

```python
>>> print('Hello World')
```
{: .nolineno}

虽然`Python`的`Hello World`也就只要一行，但是**出于尊重**还是别太抽象了，老老实实建个文件。

单击左上角的**File-New File**（macOS虽然不在左上角，但是就在最上方的**状态栏**，而且排版和Windows版**完全一样**，如果你不知道，应该**关掉这个教程**去补习macOS教程），此时会出现一个没有`>>>`的界面：

![](https://pic.imgdb.cn/item/67033ab1d29ded1a8cccbea3.png)
_文件编辑界面_

在这里输入

```python
print('Hello World')
```
{: .nolineno}

千万不能自作主张地删掉引号或者大写`print`，这里的每个东西都有**存在的原因**。

编辑完成后，点击**File-Save**，这里默认的保存路径埋在了很深处，务必记得改到**你熟悉的位置**。

然后，在文件编辑界面，点击**Run-Run Module**，就可以看到**Hello World**了！

> 新建文件、保存文件和运行也可以用快捷键`Ctrl`/`Command`+`N`、`Ctrl`/`Command`+`S`和`F5`。
{: .prompt-tip}

此时，退出IDLE，在文件管理系统中查看你的文件，你会发现它具有一个`.py`后缀，是的，这就是`Python`源代码文件的标志。从编码上，它和`.txt`是一致的，也就是说你可以用**记事本**或**文本编辑**打开它，只不过不方便编辑了。

如果你在**Windows**上双击`.py`文件，你会发现一个黑色的窗口**一闪而过**，如果眼力好，还能看到Hello World。这是因为不装任何**其他代码编辑器**时，Windows默认以**命令行**形式运行`.py`文件，`print`语句执行完后并没有任何**阻塞语句**，故直接退出。我们后面会学习如何**阻塞命令行**。macOS就没有这种事了，文件会被**Python IDLE**打开。
## 接下来会讲？

答案是：任何程序语言共有的根基——**变量**。