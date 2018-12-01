---
title: Hexo NexT主题个性美化(1)
comments: true
categories: Hexo搭建博客
tags:
  - Hexo
  - Github
abbrlink: 4ebd7fc3
date: 2018-04-19 20:18:17
---
# NexT主题个性化设置以及美化(1)

## 引言

>上篇文章之后，我们已经成功地用Github+Hexo搭建的我们的个人博客网站，那么这篇文章博主将要带领大家来把我们的NexT主题做得更美观，更个性吧！

<!--more-->

## 主题设定

NexT主题提供的一种特性，借助于 Scheme，NexT 为你提供多种不同的外观。同时，几乎所有的配置都可以 在 Scheme 之间共用。目前 NexT 支持三种 Scheme，他们是：

- Muse - 默认 Scheme，这是 NexT 最初的版本，黑白主调，大量留白
- Mist - Muse 的紧凑版本，整洁有序的单栏外观
- Pisces - 双栏 Scheme，小家碧玉似的清新

可以通过修改NexT根目录下_config/yml文件中的schemex项，将希望启用的主题前的#去掉，将剩余两项前的#添加上即可。

## 设置作者昵称及站点描述

打开Hexo根目录，设置其中 auther 为昵称，description 为站点描述。

## 设置RSS

- 什么是RSS？ RSS是站点用来和其他站点之间共享内容的一种简易方式（也叫聚合内容），通常被用于新闻和其他按顺序排列的网站，例如Blog（博客）。

- RSS可以做什么？ 订阅博客(博客上，你可以订阅你工作中所需的技术文章；也可以订阅与你有共同爱好的作者的日志，总之，博客上你对什么感兴趣你就可以订什么)。

RSS功能设置：

- 安装插件。在Hexo根目录下启动Git Bash，执行以下命令。

```安装hexo-generator-feed插件
npm install hexo-generator-feed
```

- 添加配置。在Hexo根目录下_config.yml中添加以下配置：

```RSS插件配置
# Extensions
## Plugins: http://hexo.io/plugins/
#RSS订阅
plugin:
- hexo-generator-feed
#Feed Atom
feed:
type: atom
path: atom.xml
limit: 20
```

- 打开 主题目录 _config.yml，修改其中rss项为 /atom.xml（前面有空格）

![image](https://i.loli.net/2018/08/07/5b69a42bc5611.png)

## 菜单设置

- 打开NexT主题目录下_config.yml文件，找到menu项，可以通过添删每项前的#，来选择显示在侧边栏的菜单项，如：

![image](https://i.loli.net/2018/08/07/5b69a42bc635c.png)

其中，home代表主页，categories代表分类页，about代表关于页面，archives代表归档页，commonweal代表404页面（page not found时候显示的页面），schedule代表日程表，sitemap代表站点地图。

## 创建标签界面

- 新建“标签”界面，在Hexo根目录下执行以下命令：

```新建“标签”界面
hexo new page tags
```

执行之后，会在\source目录下创建文件夹\tags，并自动在\tags文件夹下生成文件 index.md

- 打开刚刚生成的文件\source\tags\index.md，添加tape: "tags",并修改title"tags"为“标签”，如下

![image](https://i.loli.net/2018/08/07/5b69a42bc742d.png)

为文章添加标签时，只需在文章md文件头填写 tags 即可，如：
![image](https://i.loli.net/2018/08/07/5b69a42bc8322.png)

## 创建分类界面

方法与创建标签界面极为相似。

- 新建“分类”界面，在Hexo根目录下执行以下命令：

```新建“分类”界面
hexo new page categories
```

执行之后，会在\source目录下创建文件夹\categories，并自动在\categories文件夹下生成文件 index.md

- 打开刚刚生成的文件\source\categories\index.md，添加tape: "categories",并修改title"categories"为“分类”，如下

![image](https://i.loli.net/2018/08/07/5b69a42bcd4d4.png)

为文章添加标签时，只需在文章md文件头填写 categories 即可，如：
![image](https://i.loli.net/2018/08/07/5b69a42bc3c22.png)

## 参考文章

[Hexo的Next主题配置](https://blog.csdn.net/zuoziji416/article/details/53204478 "Hexo的Next主题配置")

[NexT使用文档](http://theme-next.iissnan.com/ "NexT使用文档")

## 相关文章

[Github+Hexo搭建个人博客网站](http://ender.xin/post/b973a46b.html "Github+Hexo搭建个人博客网站")
