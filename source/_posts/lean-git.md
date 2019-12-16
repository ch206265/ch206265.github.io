起因

为了实现博客文章的及时更新，需要多端实现Hexo同步，在网上查找的大部分文章都是基于GitHub，创建分支，实现此功能的，因此便简单学习一下git的基本操作，在此做下记录。

## 初次用到的命令

本文主要参考《GitHub入门与实践》这本书，目前使用到的命令是：

1. **git status、git branch**

2. **git add、git add --all、git add --a**
3. **git commit -m "log_message"、git commit**
4. **git diff、git diff HEAD**
5. **git remote add origin sshURL、git remote rm origin**
6. **git push origin branchname**
7. **git pull origin branchname**

## 对这些命令的初步认识

1. git add、git commit、git push之见的关系，以及git diff 和git diff HEAD到底是谁和谁在比较差异。

   **通过git add、git commit、git push理解git的三个区：**

   ①工作区（working tree）②暂存区（index/stage）③本地仓库区（.git）
<img src="https://img-blog.csdnimg.cn/2019112520480633.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">

   **git diff 和git diff HEAD的区别：**

   git diff 命令可以查看当前工作树与暂存区之间的差别。
   git diff HEAD命令可以查看工作树和最新提交之间的差别。
   另外，退出git diff HEAD需要在那个窗口按`q`

2. git commit -m "logmessage"只是在引号中写一些本次commit的一些备注，简短的一句话；如果写完git commit后回车，那么会进入vim编辑器中，在界面的左上角开始可以记述详细提交信息。

   提交格式如下：

   > 第一行：用一行文字简述提交更改的内容
   >
   > 第二行：空行
   >
   > 第三行及以后：记述更改的原因和详细内容

下图是刚进入编辑器的界面，按下字母c就可以进入编辑状态：
   <img src="https://img-blog.csdnimg.cn/2019112521034670.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">
  按下字母后按照上文提到的提交格式，在左上角开始编辑；编辑完成之后按下Esc，接着连按两次大写的Z，便可退出编辑器：
   <img src="https://img-blog.csdnimg.cn/2019112521041458.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">

**最后，下面是我在使用这些命令时的一些截图，只是为了长时间不用下次看到后能够快速记起：**
   <img src="https://img-blog.csdnimg.cn/20191125205028291.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">
   <img src="https://img-blog.csdnimg.cn/20191125205043489.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">
   <img src="https://img-blog.csdnimg.cn/20191125205104115.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">
   <img src="https://img-blog.csdnimg.cn/20191125210226785.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" width="65%">
      <img src="https://img-blog.csdnimg.cn/20191125211331185.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" title="上图是测试一下git add之前working tree和暂存区(stage/index)的差别" width="65%">
      <img src="https://img-blog.csdnimg.cn/20191125205904917.png" title="上图是测试一下git add之后working tree和暂存区(stage/index)的差别——没有差别" width="65%">
     <img src="https://img-blog.csdnimg.cn/20191125205256244.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NoMjA2MjY1,size_16,color_FFFFFF,t_70" title="上图是测试一下git commit之前working tree和最新提交的差别" width="65%">
        <img src="https://img-blog.csdnimg.cn/20191125205317428.png" title="上图是测试一下git commit之后working tree和最新提交的差别——没差别" width="65%">

   > 此部分建议参考：
   >
   > - [git diff与git diff HEAD -- file - 二楼后座的专栏 - CSDN博客]( https://blog.csdn.net/u013485584/article/details/53303858)
   > - [git的三个区域工作区，缓存区，暂存区 - minolk的博客 - CSDN博客]( https://blog.csdn.net/minolk/article/details/81777467)

##  一些推荐

最后推荐一些对git基础操作总结的比较好的文章

[Git简易教程笔记（1） - Jesse_Mx的博客 - CSDN博客]( https://blog.csdn.net/Jesse_Mx/article/details/78059733)

[Git简易教程笔记（2） - Jesse_Mx的博客 - CSDN博客](https://blog.csdn.net/Jesse_Mx/article/details/78158790) 