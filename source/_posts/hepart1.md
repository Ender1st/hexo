---
title: Github+Hexo搭建个人博客网站
categories: Hexo搭建博客
tags:
  - Hexo
  - Github
abbrlink: b973a46b
date: 2018-04-16 19:12:01
---
# Github

- 是一个面向开源及私有软件项目的托管平台，不需要一分钱就可以搭建自由的个人网站
- 绑定个人域名自由、方便、快捷
- 数据安全，可以回档各个历史版本
- 发布轻松，访问速度一般，网页没有广告

<!--more-->

# 搭建环境

- 注册Github（https://github.com/）

- 成功安装node.js、npm（https://nodejs.org 已集成npm）

- 安装Git（https://git-scm.com/ 找到对应自己系统的版本下载并安装）

- 详细信息：

## 本文环境

- Windows 10 Pro x64
- node.js v8.9.3
- npm v5.5.1
- Git v2.17.0
- Hexo v3.5.0

# 搭建Github博客

## 创建仓库

&emsp;&emsp;在Github里新建名为用户名.github.io的仓库，例如用户名是Ender，库名就是Ender.github.io，将来访问网址就是http://ender.github.io（每人只能创建一个这样的仓库）

## 绑定个人域名（可直接跳过）

并非必须，用 用户名.github.io 访问也可以.
- 首先，注册一个域名。博主觉得国内的阿里云不错，价格便宜，优惠力度大，服务也好.
- 注册完域名之后添加解析，用cmd ping一下用户名.github.io获取到的ip添加到A记录的记录值，主机记录填写@。CNAME的记录值填写你的用户名.github.io，主机记录填写www。
![image](https://i.loli.net/2018/08/07/5b69a3582149c.png)
- 最后在你的Github项目目录创建一个名为CNAME的文件，里面填写你的域名。原用户名.github.io会直接跳转到新域名。

# 配置SSH key

打开Git bash，执行

```
cd ~/. ssh
```
如果提示：No such file or directory 说明你第一次使用Git.

执行
```
ssh-keygen -t rsa -C "你的邮箱地址"
```
然后连按三次回车，打开你电脑上的用户目录，找到.ssh\id_rsa.pub并复制里面内容，打开Github个人设置-> SSH and GPG keys ->New SSH key，将之前文件的内容复制到里面，Title随便填。

## 测试
用Git bash执行(邮箱不用改)
```
ssh -T git@github.com
```
如果提示re you sure you want to continue connecting (yes/no)?，输入yes，然后返回
> Hi 你的用户名! You’ve successfully authenticated, but GitHub does not provide shell access.

说明SSH配置成功。
然后执行

```
git config --global user.name "用户名"// 你的github用户名，非昵称
git config --global user.email  "邮箱"// 填写你的github注册邮箱

```


# Hexo
## 简介
- Hexo是一个简单、快速、强大的基于 Github Pages 的博客发布工具，支持Markdown格式，有众多优秀插件和主题。
- 官网：http:hexo.io
- Github：https://github.com/hexojs/hexo

## 用前准备
- 安装
```
npm install -g hexo
```
- 初始化 在电脑某个地方新建一个文件夹，名字随便取，最好不要移动。

```
cd /f/Workspaces/hexo/
hexo init
```
然后hexo会自动下载文件到这个文件夹，目录结构如下：![image](https://i.loli.net/2018/08/07/5b69a38552e24.png)
- 生成初始界面，执行
```
hexo g -s
```
会开启本地预览服务，打开浏览器访问 http://localhost:4000
我们会看到默认的很丑的主题，以及一篇自动生成的Hello World文章。
## 修改主题
默认主题比较丑，我们先来安装一个好看的主题，博主推荐 NexT主题，官网：http://theme-next.iissnan.com/ 在官网你会获得很多使用方面的帮助。
执行
```
$ cd your-hexo-site
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```
修改hexo主目录的_config.yml文件中的theme: landscape改为theme: next，然后重新执行
```
hexo g
```
来重新生成网页文件。

如果出现一些莫名其妙的问题，可以先执行
```
hexo clean
```
来清理一下public的内容，然后再来重新生成和发布。

## 上传
- 打开主目录的_config.yml文件，修改deploy部分：
```
deploy:
  type: git
  repository: git@github.com:用户名/用户名.github.io.git
  branch: master

```
- 安装插件
```
npm install hexo-deployer-git --save
```
- 打开Git bash 执行hexo d就可以提交本次所有代码到Github了。
## 保留CNAME文件
由于hexo每次提交都会将原有代码删除（包括之前创建的用于解析的CNAME文件），所以我们为了保留解析，在主页面下source文件夹中创建CNAME文件（没有后缀），其中填写你的域名，这样我们每次提交都会保留CNAME文件，让解析能够正常运行。
![image](https://i.loli.net/2018/08/07/5b69a3ad17cd5.png)

## 常用命令
常见命令
```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
```
缩写
```
hexo n  hexo new
hexo g  hexo generate
hexo s  hexo server
hexo d  hexo deploy
```
组合命令

```
hexo s -g #生成并本地预览
hexo d -g #生成并上传
```
## 写博客
在hexo根目录下运行Git bash（在文件夹右键，选择Git Bash Here），执行
```
hexo n "name"   #名称内不要有空格、汉字
```
打开生成的文件
![image](https://i.loli.net/2018/08/07/5b69a3d44935e.png)

一般完整格式为
```
---
title: postName #文章页面上的显示名称，一般是中文
date: 2013-12-02 15:30:16 #文章生成时间，一般不改，当然也可以任意修改
categories: 分类 #分类
tags: [tag1,tag2,tag3] #文章标签，可空，多标签请用格式，注意:后面有个空格
description: 附加一段文章摘要，字数最好在140字以内，会出现在meta的description里面
---

以下是正文

```

## 让博客主页显示博文一部分

在合适地方加上

```
<!--more-->
```

在目录上就会在添加的位置截取，显示阅读全文按钮。

# 参考文章

[使用hexo+github搭建免费个人博客详细教程](http://blog.haoji.me/build-blog-website-by-hexo-github.html?from=xa)

# 相关文章

[Hexo NexT主题个性美化(1)](http://ender.xin/post/b973a46b.html)