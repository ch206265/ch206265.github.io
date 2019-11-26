---
title: 初次安装Ubuntu18.04
date: 2019-11-25 16:51:11
tags:
- Ubuntu
- Linux
categories: 学习工具
mathjax: false
---

 2019/11/23 15:34 

 主要解决的问题：
1、解决 “明明C盘还有几十G可以使用但是创建压缩卷时可压缩竟然是0”
2、解决“安装完之后才知道是UEFI启动模式，Easy BCD新添加条目变成灰色不可用”

# 一、设备情况
双硬盘电脑：固态硬盘（win系统盘）+机械硬盘
BIOS模式：UEFI

<!--more-->

# 二、准备工作
## 1、下载Ubuntu镜像
我是直接拷贝了同学的；你也可以从下面的网址中下载
[系统下载 | Ubuntu](https://cn.ubuntu.com/download) 
## 2、在磁盘中压缩出未分配的空闲区域
安装Ubuntu需要分配四个磁盘分区分别给“/”、“/home”、“swap”和“/boot”。
（具体分配体现在安装过程，现在这一步骤只是先把他们需要的磁盘空间给压缩出来）
其中，挂载点“/”是Ubuntu系统盘相当于win系统的C盘；
挂载点“/home”是用户文件夹，相当于win系统的Users；
挂载点“swap”是交换空间，相当于win的虚拟内存；
而挂载点“/boot”则是Ubuntu的启动引导空间。
（[什么是分区/主分区/逻辑分区/挂载点](https://blog.csdn.net/lin353809836/article/details/86747491)）
由于电脑是双硬盘，固态硬盘（win系统盘）+机械硬盘，压缩出分配给这四个挂载点的磁盘空间时需要注意以下几点：
### 注意1：在机械硬盘和装win系统的固态硬盘上分别压缩出一个空闲区域
机械硬盘上压缩出一个较大空闲区域后，在win10系统盘（固态）上再压缩出大约500MB的空闲区域。
机械硬盘上压缩出来的空闲空间主要分配给：挂载点“/”、“/home”、“swap”；
在装win系统的固态硬盘上压缩出的空间分配给挂载点“/boot”。
- 为什么不把挂载点“/”、“/home”、“swap”和“/boot”的分配统一放在固态盘或者机械盘？
  统一放在固态盘就和win系统装在一起了，能不在一起就别再在一起；
  统一都放在机械硬盘中，“/boot”分区没在win的系统盘，容易开机引导失效，具体描述就在下面⬇
- 为什么挂载点“/boot”分区要和win系统盘在一起？
  参看[这篇博文](https://blog.csdn.net/qq_24624539/article/details/81775635)的讲解，如果不这么办，会出现Ubuntu开机时光标一直在左上角闪烁无法进入系统的问题，我按照博文中的描述，一次就安装成功了，没有出现左上角光标一直闪烁开机引导失效的情况。
### 注意2：明明C盘还有几十G可以使用但是创建压缩卷时可压缩竟然是0怎么办
  一般情况下，我们使用[win10自带的磁盘管理功能](https://jingyan.baidu.com/article/425e69e6bbd0c7be14fc164a.html)就可以从磁盘上压缩出空闲空间，但是也有一些例外。
明明C盘还有几十G可以使用但是创建压缩卷时可压缩竟然是0？？我遇见了……网上查了一些方法，比如磁盘清理，清了的确不少的东西，但是还不行；又有人说磁盘清理之后要碎片整合，也搞了，还是不行。所以，最后用——DiskGenius了。
在我多次使用过程中偶然发现，用过DiskGenius后，再用win10磁盘管理中自带的“压缩卷”功能时，可压缩空间突然变多了，已经不是0了……，这样再调整压缩空间大小的时候就不必用DiskGenius，每次重启进入PE了。
## 3、安装开机引导程序，Easy BCD或者Easy UEFI
[EasyBCD - Download](https://easybcd.en.softonic.com/) 
[EasyUEFI - Download](https://easyuefi.en.softonic.com/) 
## 4、制作U盘启动盘
[Create a bootable USB stick on Windows | Ubuntu tutorials](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0) 
## 5、进入BIOS中，将开机启动设置为从U盘启动
设置方法，[参考此链接](https://jingyan.baidu.com/article/1974b289ebb809b4b0f7747d.html)
# 三、安装过程
安装过程主要参考这篇博文：
[Win10+Ubuntu18.04双系统安装指南（一）（实操真谛） - 索命的博客 - CSDN博客](https://blog.csdn.net/u013052326/article/details/81545449) 
[Windows + Ubuntu 16.04 双系统安装详细教程 - flyyufenfei的博客 - CSDN博客](https://blog.csdn.net/flyyufenfei/article/details/79187656) 
简单总结以下需要注意的点有：
## 1、断网
安装过程需要断网吗？讲道理都可以，但是断网的话在安装的时候不检查更新了，安装的更快，并且在[这篇文章](https://blog.csdn.net/qq_24624539/article/details/81775635)中说到，16.04安装时必须断网（原文说是“拔掉网线”），不然会导致“选地图处安装程序卡死、安装失败”。因此我是断网安装的（但是安装的是18.04），安装成功。
## 2、 键盘布局
什么的这些设置按照默认，英语（美国）就行了
## 3、 “更新和其他软件”
“更新和其他软件”这一步，
选择“最小安装”，
去掉“安装Ubuntu时下载更新”，
勾选“为图形或无线硬件，以及其他媒体格式安装第三方软件”
（在没有网的情况下这么设置，并且这样在安装的过程中就不会自动检查更新了，提高了安装的速度）
## 4、“安装类型”
“安装类型”这一步选择“其他选项”自己创建调整分区，随后便进入到自己创建分区的关键环节，
需要创建前文提到的“/”、“/home”、“swap”和“/boot”四个分区，前三个建在机械硬盘的那个空闲空间中，“/boot”分区创建在固态硬盘的空闲空间中，其中“/boot”分区比较关键一点，容易出错。
在这一步，EFI引导和boot引导的设置有所不同，需要根据自己设置的启动方式确定。
总体来讲，如果是Bios的启动模式是UEFI，对应EFI引导，则不需要"/boot"，创建分区的时候“用于”设置为“EFI系统分区”：图片来自：https://blog.csdn.net/flyyufenfei/article/details/79187656
![图片来自](https://img-blog.csdnimg.cn/20191123205218727.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70)
Bios的启动模式如果是Legacy，对应的就要设置Boot引导，需要创建“/Boot”分区：
图片来自：https://blog.csdn.net/flyyufenfei/article/details/79187656
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123205312600.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70)
其他分区根据自己需要结合参考文章进行设置，这里不再总结了。
## 6、“安装启动引导器的设备”
然后不要直接点击”安装“，还是在进行分区设置的界面左下方，有一个“安装启动引导器的设备”的设置选项。
这里如果是EFI引导的话，选择EFI引导对应的分区；
若是Boot引导的话，就选择”/boot“分区所在的设备。
图片来自：https://blog.csdn.net/flyyufenfei/article/details/79187656
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123205402915.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70)
## 7、 最后
最后会出现一个你配置好的分区表让你检查是否有误，无误后继续；
然后会出现个地图让你选择地域（选上海）；
然后设置键盘布局，设置设备名称/账号名称/开机密码等；
最后进入到安装状态；
安装完成后，拔下U盘重启，更改Bios的启动项为原来的“操作系统的启动管理员”。
# 四、使用Easy BCD或者Easy UEFI进行引导设置
由于我安装的时候没有意识到自己是UEFI模式，完全按照网上的教程只在固态盘创建了个”/boot“分区，然后[参考这篇博文](https://blog.csdn.net/flyyufenfei/article/details/79187656)，使用Easy BCD的时候才有所提示，并且新添加条目时都是灰色：
（图片来自：https://blog.csdn.net/qiusuoxiaozi/article/details/72807104）
![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123205515964.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70)
此时我以为自己第一次安装要凉了，结果网上搜到有讲，可以使用Easy UEFI进行引导，并按照[这篇博客](https://blog.csdn.net/www_helloworld_com/article/details/84672165)完成了引导设置（只看Easy UEFI的使用这部分就可以了）。
但是有一个比较奇怪的地方，我在Easy UEFI中找之前boot分区(或者efi系统分区)所在的那500MB空间时无法选中，但是在固态硬盘中还有一块260MB的efi分区，在这个分区中找到了`grubx64.efi`（这个貌似是windows的efi引导区）我也不知道为什么……
最终重启后出现了让选择启用那个系统的界面，直接回车就进入到了Ubuntu系统，然后自动提示需要更新以下所选择语言的一些东西，具体是什么忘记了……
第一次安装就这么“成功”了，限于自己的认识，这可能并不是真正的成功，或许有很多隐藏的小隐患……但是，只能先这样用着了，毕竟目前也没什么问题出现……此外，这只是针对自己遇到的情况的一些总结，并不具有普遍性……
**注**：由于我以为在Easy UEFI中选择了那个260MB的分区进行引导，故而500MB的那个没有用了，就把500MB的分区给格式化了，然后悲剧就来了，引导崩溃了，显示`Minimal BASH like line editing is supported. For the first word, TAB lists possible command completions. anywhere else TAB lists possible device or file completions.`错误，导致我win10和ubuntu两个系统都无法进入了，最后从[这篇文章](https://blog.csdn.net/heroacool/article/details/50817856)中找到了[解决办法](https://www.linuxidc.com/Linux/2015-07/120748.htm)，使用`bootrepair`,但是这个工具也只能让我从新进入到win10中，ubuntu还是没法进入，无奈就重新安装了（除了这次手抽，应该还算是一次安装成功`^_^`）。重新安装后就注意到自己是UEFI 模式了，就专门在500MB 的分区选择`efi系统分区`，但是奇怪的是，在用Easy UEFI引导的时候500MB 的那个分区仍然是不可选的，无奈还是选择了260MB的那个……
# 五、ubuntu系统安装好后
https://blog.csdn.net/Jesse_Mx/article/details/52816928
[安装Ubuntu后必须要做的几件事(一)](https://blog.csdn.net/day_to_die/article/details/78689999)