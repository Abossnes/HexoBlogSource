---
title: Hexo--yilia plus theme notes
date:  2021-02-13 21:57:10
toc: true
categories: hexo
tags: hexo
description: hexo配置笔记
---

#### 1.常用命令

```yml
hexo s  //本地启动hexo命令
hexo new xxx //新建文章;默认source/_posts/xxx.md
hexo new page cc //在source目录下新建文件夹cc,其中默认index.md ,访问其路径http://localhost:4000/cc
hexo clean && hexo g && hexo d  //hexo发布git命令

https://hexo.io/zh-cn/docs
```

#### 2.给文章添加分类和标签

```
title: 在这里
date: 2018-08-02 11:41:10
tags:
- 博客           //多个标签可以这样添加
- hexo
categories: web前端
```

#### 3.文章添加目录

```yml
# 1._config.yml中添加如下配置

# 目录设定：0-不显示目录； 1-文章对应的md文件里有toc:true属性，才有目录； 2-所有文章均显示目录
toc: 2
# 根据自己的习惯来设置，如果你的目录标题习惯有标号，置为true即可隐藏hexo重复的序号；否则置为false
toc_hide_index: true
# 目录为空时的提示
toc_empty_wording: '目录，不存在的…'  

jsonContent:
  meta: false
  pages: false
  posts:
    title: true
    date: true
    path: true
    text: false
    raw: false
    content: false
    slug: false
    updated: false
    comments: false
    link: false
    permalink: false
    excerpt: false
    categories: true
    tags: true

# 2.安装依赖
npm i hexo-generator-json-content --save

```

