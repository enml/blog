---
layout: post
title: "jekyll加载图片的路径问题"
description: ""
category: 技术分享
tags: [路径]
---
{% include JB/setup %}
# jekyll加载图片的路径问题
---
　一开始使用根目录` /assets/…/img/bg.png `的方式，在localhost调试成功，但在github pages失败。
　后来试了一下当前目录方式` ./img/bg.png `成功。也可以用` img/bg.png `表示当前目录。

<!--break-->
