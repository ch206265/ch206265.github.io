---
title: 多终端同步Hexo博客
date: 2019-11-22 01:14:07
tags:
- git
- hexo
- 建站笔记
categories: 学习工具
mathjax: false
---

记录一下实现多终端同步Hexo博客的一些操作，学习的过程中意外学习了一些git的基本操作，并记录在另外一篇博文中。

# 整体思路

整体思路和流程主要参考以下两篇文章：

> [利用Hexo在多台电脑上提交和更新github pages博客 -简书](https://www.jianshu.com/p/0b1fccce74e0) 
> [如何解决github+Hexo的博客多终端同步问题 - monkey_lzl的博客 -CSDN博客](https://blog.csdn.net/monkey_lzl/article/details/60870891)

然后，在新电脑上需要重新安装git、node.js、Hexo环境、以及生成SSH添加到GitHub，这些设置参考下面文章的相应内容即可：

> [hexo史上最全搭建教程 - Fangzh的技术博客 - CSDN博客](https://blog.csdn.net/sinat_37781304/article/details/82729029)
> [生成新 SSH 密钥并添加到 ssh-agent - GitHub 帮助](https://help.github.com/cn/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

详细的步骤就不写了，根据下面总结的思路配合上面的提到的参考文章，相信如果下次还需要进行这样的操作，也会很快就熟悉了。下面总结一下主要思路：
**首先需要知道Hexo在本地和在GitHub上的文件是两个不同的东西。本地的主要是部署文件包括了自己写的所有文章的MarkDown文件，主题文件等等；上传到GitHub中的文件是部署文件渲染过后的文件，我们最终访问GitHubName.github.io看到的个人站点其实就是这些保存在GitHub中渲染过的东西。想要实现多端同步，关键点是让多台电脑上都有最新的部署文件，也就是那个本地文件，因此我们可以利用git实现这一需求。**

# 大致流程

1. 到GitHubName.github.io这个仓库，新建分支命名为hexo（这个新建的branch就是为了存储本地的部署文件），并将新建的hexo分支设置为default分支；
2. 然后在老电脑上（有本地部署文件的电脑）使用git clone，把hexo仓库克隆下来，再把部署文件全部复制粘贴进这个克隆下来的hexo文件夹中（最好使用clone吧，刚开始我是直接把那个仓库的ZIP压缩包下载下来了，但是在某一步一直会报错）；
3. 按照上面的思路分析，我们最终目的是要将hexo的本地部署文件上传到GitHub上，所以按顺序依次使用git init、git add、git diff HEAD、git commit、git remote add origin sshURL 、git push origin hexo等命令，就可以把最新粘贴进分支hexo中的部署文件同步到GitHub中了。这个
  过程出现的大多数问题应该是由于不熟悉这些git命令造成的。

> 我刚开始尝试时遇到过这些问题： 
> 1. [github连接远程仓库时出现Warning: Permanently added the RSA host key for IP address *********** ...... - comeonbabe_的博客 - CSDN博客](https://blog.csdn.net/comeonbabe_/article/details/80244854) 
> 2. [Git提交时提示‘The file will have its original line endings in your working directory’ - 刘俊涛的博客 - 博客园](https://www.cnblogs.com/lovebing/p/7121754.html)  
> 3. [Git 提示fatal: remote origin already exists错误解决办法 - Ricky - CSDN博客](https://blog.csdn.net/top_code/article/details/50381432)  
> 4. 在gitBash中，复制粘贴的快捷键不是CtrlC/V 
> 5. [git push 失败出现error: src refspec master does not match any.解决方案 - 青阳十五的专栏 -CSDN博客](https://blog.csdn.net/yemoweiliang/article/details/52980658)  
> 6. [git error - "error: src refspec master does not match any." -Stack Overflow](https://stackoverflow.com/questions/23957836/git-error-error-src-refspec-master-does-not-match-any)  
> 7. [warning: LF will be replaced by CRLF in 解决办法 -csdn799316120的博客 - CSDN博客](https://blog.csdn.net/csdn799316120/article/details/79565579)  
> 8. [git commit之后进入vim（vi）界面，如何退出 -Amos_luoye的博客 - CSDN博客](https://blog.csdn.net/Amos_luoye/article/details/88292438)  
>    <br/>其中更详细的了解可以看下总结的git基本操作那篇总结。

4. 然后在新电脑上安装git、node.js、Hexo环境、以及生成SSH添加到GitHub。
5. 新电脑上的准备工作就绪之后，把hexo分支git clone下来，然后就可以和在原来电脑上一样进行写作了。写完之后一般按照 git init、git add、git diff HEAD、git commit、git remote add origin sshURL 、git push origin hexo。其中git remote add origin sshURL也不必每次都弄。
6. 上一步只是把最新的部署文件上传到了GitHub中，但是并没有对其渲染，所以还得依次执行Hexo 的命令：hexo clean 、hexo g、hexo s、hexo d。
7. 最后，这样就可以在两台电脑上都写最新的文章并及时发布了。但是在每台电脑上，开始写博客之前，最好都使用git pull origin hexo从GitHub中把最新的部署文件获取下来。

过程基本就是这样。
