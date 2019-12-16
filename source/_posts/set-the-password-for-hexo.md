---
title: npm install包运行出错
date: 2019-11-25 16:51:53
tags:
- hexo-blog-encrypt
- hexo-encrypt
- 建站笔记
categories: 学习工具
mathjax: false
---

最近想要给博客文章做个加密，一开始也是无从下手，但是还好有篇博文：[Hexo 博客加密功能添加 | Hailiang's Blog](http://zhailiange.com/2017/07/06/hexo-encrypt/)
这里面介绍了两个博客加密插件`hexo-blog-encrypt`和`hexo-encrypt`
最初按照介绍，安装`hexo-blog-encrypt`但是遇到了困难

<!--more-->

![npm warn](https://img-blog.csdnimg.cn/20191123211617597.png)

```bash
$ npm install
npm WARN babel-eslint@10.0.3 requires a peer of eslint@>= 4.12.1 but none is installed.
You must install peer dependencies yourself.
```
不知道是什么意思，上网搜索了一下，找到了这篇博文：[npm install 包运行出错 - 德尼的博客 - CSDN博客](https://blog.csdn.net/qq_43153418/article/details/88380082) ，直接复制了里面的答案：

```bash
npm install eslint@4.x babel-eslint@8 --save-dev
```
但是一直成功不了，知道看到了[这篇文章](https://blog.csdn.net/qq_37336604/article/details/80359808)，才明白了报错的含义，就是在`package.json`中缺少了两个依赖：
```bash
"babel-eslint": "^10.0.3",
"eslint": "^4.12.1"
```
需要我们手动安装……而之前直接复制的`npm install eslint@4.x babel-eslint@8 --save-dev`
其实也是安装这两个依赖的，但是，它安装好后是直接在`package.json`中新写一个`dependencies`，没和原来的格式进行合并。
最后，现在虽然装好了，但是也还发现了个bug，就是对于有目录的文章，`hexo-blog-encrypt`这个插件会使侧边的目录导航栏显示失效。