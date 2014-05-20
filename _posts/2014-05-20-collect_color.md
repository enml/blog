---
layout: post
title: 收藏颜色
category : python_django
tagline: "Supporting tagline"
tags : [python, django]
---
{% include JB/setup %}
# 收藏颜色的工具
---
![collect_color](http://enml.github.io/blog/image/collect_color.jpg)


用了三个小时完成了上图的功能，满足了我的需求。

只要在输入框输入颜色数值，便可记录到数据库，并把颜色作为该数值背景色输出页面。

<!--break-->

本来是在寻找一个可以保存自己喜欢的颜色的工具，一开始想着记录在onenote，但是只能记录数值，不够直观。如果把图片粘贴过去会很繁琐并且不够雅观。后来把颜色直接合并在一张图上，但记录时每次都需要进行图片修改，繁琐也依然不美观。中午午睡后百度了一下是否有相关的在线工具，一无所获。突然想着要不自己搞一个吧！在脑海里构建了一下基本框架后觉得可行，便开始编写代码。花了三个小时总算实现了。

