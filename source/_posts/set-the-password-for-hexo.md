---
title: 给Hexo博客设置访问密码
date: 2019-11-25 16:51:53
tags:
- hexo-blog-encrypt
- hexo-encrypt
- 个人建站
categories: 学习工具
mathjax: false
---

 2019/11/06 00:37 

最近想要给博客文章做个加密，一开始也是无从下手，但是还好有个博客：

[Hexo 博客加密功能添加 | Hailiang's Blog]( http://zhailiange.com/2017/07/06/hexo-encrypt/)

这里面介绍了两个博客加密插件

[hexo-blog-encrypt](https://github.com/MikeCoder/hexo-blog-encrypt)和[hexo-encrypt](https://github.com/edolphin-ydf/hexo-encrypt)

最初按照介绍，安装hexo-blog-encrypt但是遇到了困难

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191123211617597.png)

```git bash
$ npm install npm WARN babel-eslint@10.0.3 requires a peer of eslint@>= 4.12.1 but none is installed. You must install peer dependencies yourself. 
```

因为完全是小白，不知道是什么意思，上网搜索了一下，找到了这篇博文：

[npm install 包运行出错 - 德尼的博客 - CSDN博客](https://blog.csdn.net/qq_43153418/article/details/88380082) 

直接复制了人家给的答案：

```git bash
npm install eslint@4.x babel-eslint@8 --save-dev 
```

但是一直成功不了。

知道看到了下面这篇文章，

[npm WARN eslint-plugin-react-native@3.2.1 requires a peer of eslint@^3.17.0 || ^4.0.0 but none - qq_37336604的博客 - CSDN博客]( https://blog.csdn.net/qq_37336604/article/details/80359808)

才明白了报错的含义，就是在package.json中缺少了两个依赖，

```git bash
"babel-eslint": "^10.0.3", "eslint": "^4.12.1" 
```

需要我们手动安装……

而之前直接复制的

```git bash
npm install eslint@4.x babel-eslint@8 --save-dev 
```

其实也是安装这两个依赖的，但是，它安装好后是直接在package.json中新写一个dependencies，没和原来的格式进行合并。

现在虽然装好了，但是也还发现了个bug，就是对于有目录的文章，[hexo-blog-encrypt](https://github.com/MikeCoder/hexo-blog-encrypt)这个插件会使侧边的目录导航栏显示失效。