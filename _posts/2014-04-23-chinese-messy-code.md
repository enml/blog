---
layout: post
title: "解决invalid byte sequence in GBK"
description: ""
category: 技术分享
tags: [gbk,乱码]
---
{% include JB/setup %}
# 解决invalid byte sequence in GBK
---

　jekyll对中文的支持不太好，导致经常出现乱码甚至无法运行`jekyll server`命令。解决post内容乱码问题可以通过修改convertible.rb文件的第27行：

```
self.content = File.read(File.join(base, name));
```
为

```
self.content = File.read(File.join(base, name), :encoding => "utf-8");
```

　原因File.read()可能采用系统默认编码读取文件，中文系统为GBK，但markdown文件均为utf-8编码，所以导致无法正确展现中文。

<!--break-->

　但是当我在post.html模板里面加入中文之后，`jekyll server`命令直接报错。解决办法是在运行服务器前先运行`chcp 65001`命令，即可解决。在官方找到的解决办法**Windows users: run chcp 65001 first to change the command prompt's character encoding (code page) to UTF-8 so Jekyll runs without errors.**
