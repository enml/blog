---
layout: post
title: GitHub基础入门
category : 技术分享
tagline: "Supporting tagline"
tags : jekyll, github
published: false
---
{% include JB/setup %}

# GitHub Pages（像黑客一样写博客）

`技术`

---

是的，之前github的名字其实早已经如雷贯耳，只是我对它望而生畏，始终不敢去触碰它。因为它咋一看上去冷冰冰的，眼之所及，皆为代码；并且又找不到能详细却直观地描述它的理念的教程，所以我始终无从下手。

终于，两天前看到**Blogging like a hacker**这篇文章，决定试试搭建一个基于**github pages**的blog，遂开始尝试。

<!--break-->

首先下载`github`的windows客户端，客户端很简约，这个非常值得称赞。客户端登录后会直接跟你github账号进行绑定同步，因此你能直观的看到github上你的项目文件。硬着头皮尝试各种git命令，不求甚解。以前我很讨厌这种不求甚解的状态，当我在阅读一篇教程时总是希望先了解一下基本脉络，当差不多头脑里有个整体框架后再动手，这样的好处就是你知道你每一步是在做什么，成功率也比较高。但并不是每一篇教程或者每一个项目你都能很快地掌握其基本脉络，就像github。很多教程基本就是直接说输入

>```git push origin master```

之类的，但他没告诉我输入之后能干什么，会发生什么。更没有人告诉我每一次必须先commit message才能提交。所以我只能糊里糊涂地跟着教程走，不过尝试了几遍之后，也就大概理解了脉络。

* github为版本控制系统。也就是说，你每一次的提交都会有相关的标记，以便进行回滚和协作。
* 对于远程代码，可以通过```git clone```语句进行clone，可以clone到本地库，也可以clone到github库中。
* 对于本地代码，可以通过```git remote set-url```语句绑定到对应的repository；也可以通过客户端里的public推送到github上。
* 每一次push前必须先commit -m，客户端里是填写相应的summary。