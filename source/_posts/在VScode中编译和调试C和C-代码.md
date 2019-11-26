---
title: 在VScode中编译和调试C和C++代码
date: 2019-08-06 23:01:57
tags:
- VScode
- C/C++
categories: 学习工具
mathjax: false
---

过程如下：

## 安装VS code
## 安装插件

![chinese(Simplified) Language pack for VScode](https://raw.githubusercontent.com/ch206265/BlogPictures/master/20190806230417.png)<!--more-->
![C/C++](https://raw.githubusercontent.com/ch206265/BlogPictures/master/20190806230510.png)
![Code Runner](https://raw.githubusercontent.com/ch206265/BlogPictures/master/20190806230541.png)

## 下载MinGW并配置环境变量
- 官网下载[[下载]](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/?tdsourcetag=s_pctim_aiomsg)
- 配置环境变量，参考这篇文章：[如何安装MinGW - 简书](https://www.jianshu.com/p/ee1ccb0a3062)

**讲道理，此时应该就可以运行程序了，接下来是调试**
## 调试（即，配置.vscode文件）
注意：文件名和路径名最好全是英文
- 新建文件，需要调试的源文件放到此文件夹中，然后右键，选择`Open with Code`
- 点击debug图标，打开launch.json并修改
- 该文件夹内，新建文件`tasks.json`，并完善内容

##  完工，F5可以进行调试
- 程序最后加一个`getchar();`，或者加`system("pause");`等避免调试后黑框闪没

## 参考资料

编译和运行：[零基础 | 如何用VS Code写C/C++程序 - 安装与配置 - 简书](https://www.jianshu.com/p/86313c6a1e0e) 
调试：[Visual Studio Code (vscode) 配置C、C++环境/编写运行C、C++（Windows）【真正的小白版】 - 一苇以航 - CSDN博客](https://blog.csdn.net/bat67/article/details/81268581) 

<a href="https://bestzuo.cn" class="LinkCard">Sanarous的个人博客</a>

