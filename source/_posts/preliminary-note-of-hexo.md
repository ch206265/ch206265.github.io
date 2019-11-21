---
title: hexo笔记
date: 2019-11-09 00:56:24
tags: 
- hexo 
- 建站笔记
categories: 工具使用
mathjax: false
---

关于hexo博客的搭建之前参考了很多优秀的博文，当时按照文中的指导大多数想要的功能都可以实现，但是功能以实现我懒癌就犯，时间一久，就不知道当初是怎么操作的了，还得从头搜索。这里先把他们罗列出来，有机会的话再对其进行一些总结。

<!--more-->

1、[hexo+github搭建个人博客(超详细教程)](https://blog.csdn.net/AinUser/article/details/77609180)

主要参照这篇博文下载安装了git、node.js以及使用git初次安装hexo

2、[hexo史上最全搭建教程](https://blog.csdn.net/sinat_37781304/article/details/82729029)

这篇文章从三个方面介绍怎么基于GitHub搭建hexo博客我也对应进行了一些操作。

第一部分：hexo的初级搭建还有部署到github page上，以及个人域名的绑定

按照上篇文章安装好git、node.js、hexo后可以参考这篇文章接着，

1. GitHub上建立存储博客的个人仓库

2. 生成SSH添加到GitHub上

3. 将hexo部署到GitHub上，但是后面的个人域名绑定没有做；

第二部分：hexo的基本配置，更换主题，实现多终端工作，以及在coding page部署实现国内外分流

**首先，hexo的基本配置**

1. 介绍了文件根目录下的_config.yml文件；

2. front-matter则是设置markdown博客文件开头，采用统一的yaml格式，用三条短横线分隔，就是用_ _ _把它与博客正文分开的那部分，主要是设置文章属性，比如标题title、创建日期date、修改日期updated、标签tags、分类categories、是否开启评论comments等等基本信息(它其实有模板，每次新创建文章是可以自动生成这个文章开头的属性设置，新建文档的头部的模板：scaffold文件夹下的post.md，在这里面修改一下，以后新建的博客文档头部都会是这个样式)

3. layout，是hexo的布局设置，三种默认布局：post、page、draft，对应的文件夹是source/_posts、source、source/_drafts

我们平时创建新文章使用的

`hexo new filename` 

完整版其实应该是

`hexo new post filename `

只不过hexo默认的layout布局是post而已

创建草稿的话可以用这个命令

`hexo new draft filename  `

草稿写完了发布草稿的时候可以

`hexo publish draft filename	 `

**其次，更换主题**

1. GitHub上下载主题；

2. 下载的主题放在根目录的theme文件夹下

3. 在根目录的配置文件_config.yml中找到theme关键字的设置，把它改成新添加的主题的名字

4. 然后每个主题里面也有自己主题的一些配置设置，也在_config.yml文件中，但是这个文件是在主题文件夹目录下面的，和之前的那个在根目录下的还不一样

除了更换主题外，这篇文章在这一部分还介绍了，在菜单栏新增菜单选项、添加RSS订阅等

**最后，git分支进行多终端工作以及在coding page上部署实现国内外分流**，但是这两部分没有参照这篇文章

第三部分：hexo添加各种功能，包括：

1. 百度搜索和Google搜索的SEO；

2. 评论系统，只是介绍了一下，来比力，valine，等，但是我最后用的评论系统是git talk

3. 添加百度统计

4. 文章阅读量统计，leanCloud

5. 引入不蒜子访问量和访问人次统计

关于这文中方面推荐文章：

[Hexo博客添加SEO-评论系统-阅读统计-站长统计](http://visugar.com/2017/08/01/20170801HexoPlugins/)

[Hexo框架之GitHub博客搭建及SEO站点收录](https://www.jianshu.com/p/9be9b4786f97)

[解决github博客SEO的问题 - coderzhw - 博客园](https://www.cnblogs.com/coderzhw/p/11109333.html) 

![百度资源站的链接提交](https://raw.githubusercontent.com/ch206265/BlogPictures/master/20191109010522.png)



这里有一个百度资源站的链接提交，这个和站点的SEO好事有区别的，这个相当于是可以直接提交博文的网址链接。可以直接点击菜单栏右侧的“用户中心”，在那里面会出现

![百度收录](https://raw.githubusercontent.com/ch206265/BlogPictures/master/20191109010532.png)

（[百度搜索资源平台](https://ziyuan.baidu.com/site/siteadd)）然后按照前面的两篇关于网站SEO的文章进行优化即可。需要注意的是Github禁掉了百度的爬虫，使用GitHub建立的博客无法被百度收录，所以在进行验证的时候验证不成功。

![验证失败](https://raw.githubusercontent.com/ch206265/BlogPictures/master/20191109010722.png)

貌似想要被收录可用用CDN，让百度蜘蛛从CDN的网址爬取博文；再或者就是双写，在其他博客平台上发布相同的文章，然后给出GitHub博客的链接。

3、[Hexo even主题博客配置](https://blog.csdn.net/meifannao789456/article/details/81673816) 

可能比较有用的就是介绍了一下hexo的文件结构以及各个主题文件的文件结构

4、[给hexo主题添加背景及更改字体颜色（next的Mist主题）](https://blog.csdn.net/weixin_40837922/article/details/88047241)

5、[hexo 新建一篇文章给它添加分类和标签](https://blog.csdn.net/qq_25560423/article/details/53785411)

[hexo添加新菜单](https://blog.csdn.net/weixin_44539392/article/details/86621999)

新建文档的头部的模板：scaffold文件夹下的post.md，在这里面修改一下，以后新建的博客文档头部都会是这个样式

6、[解决 Hexo 搭建博客显示不出分类、标签问题](https://blog.csdn.net/Wonz5130/article/details/84666519)

7、[文章的输入密码访问设置](https://blog.csdn.net/kunkun5love/article/details/79130956)

8、[hexo next主题解决无法显示数学公式](https://blog.csdn.net/yexiaohhjk/article/details/82526604)

9、[Hexo 入门指南（三） - 文章 & 草稿](https://blog.csdn.net/wizardforcel/article/details/40684575)

主要是讲解了文章的title、date、tags、categories等基本属性设置，摘要设置<!--more-->以及草稿设置

10、[Hexo 解决网站名中文乱码](https://blog.csdn.net/qq_21808961/article/details/84475555)

11、[Hexo博客NexT主题开启文章目录和调整样式](https://blog.csdn.net/wugenqiang/article/details/88609066)

12、[GitTalk评论配置](https://blog.csdn.net/madridcrls7/article/details/80871596)

13、[使用github OAuth实现用户登录](https://blog.csdn.net/kobe24lmlps/article/details/80838329)

14、[hexo的next主题个性化教程：打造炫酷网站](https://blog.csdn.net/qq_33699981/article/details/72716951)

关于最开始探索建站的记录基本到这里也就结束了，但是，在这个过程中，也见识了一些十分优秀的个人站点，有的是界面设计的超级漂亮，有的是博客的内容十分吸引人。此外，在这些优秀的个人站中，博主们也会分享一些他们自己的建站经验，也是很好的学习素材。