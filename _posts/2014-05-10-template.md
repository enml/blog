---
layout: post
title: Template
category : python_django
tagline: "Supporting tagline"
tags : [python, django,template]
---
{% include JB/setup %}
# Template
---

**在view里面，我们获取了相关的数据，但我们的目的是将数据呈现出来。**


于是：

**1.首先我们想到的是直接把数据硬编码到html代码里面，然后通过`HttpResponse`对象传递给浏览器进行渲染：**

```
from django.http import HttpResponse
import datetime

def current_datetime(request):
    now = datetime.datetime.now()
    html = "<html><body>It is now %s.</body></html>" % now
    return HttpResponse(html)
```
<!--break-->

但是很明显这种方法不适合生产环境，你不可能把整个html页面都硬编码在view里面，因为这显得既愚蠢又低效。对于template的改动很明显要比view频繁得多，这种方式意味着你想更改页面表现时都必须得改动python代码，并且前后端无法同步开发。于是有了第二种方式：



**2.把html代码分离成独立的模板，通过加载模板文件进行渲染，这样可以实现前后端分离：**


``` python
   #view
from django.shortcuts import render_to_response
import datetime

def current_datetime(request):
    now = datetime.datetime.now()
    return render_to_response('current_datetime.html', {'current_date': now})

```


```
#template
<html><body>It is now {{ current_date }}.</body></html>
```
通过render()传递数据给template的方式在上一篇文章有列举出来。这种模式的好处很明显。但我们又遇到一个问题：**假如我的网站有100个页面，那我是不是要写100个template呢？** 

我们知道这样是愚蠢。编程中有一个很重要的思想就是--**最大限度地实现代码重用。** 而我们写100个页面的重复代码可能已经超过40%了，这不但费时费力，你还可能见笑于大方之家。所以我们有一种优雅的解决方式：**include**

**(1). 把重用代码分离出来，比如header.html,footer.html,sidebar.html；然后`include`到content.html中。**

```
# header.html

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html lang="en">
<head>
    <title>The current time</title>
</head>
```

```
    # footer.html

        <p>Thanks for visiting my site.</p>
    </body>
    </html>
```

```
# include 'header' and 'footer'

{ include 'header.html' %}
<body>
    <h1>My helpful timestamp site</h1>
    <p>It is now {{ current_date }}.</p>
{ include 'footer.html' %}
```

没错，这样很优雅，可以实现代码重用。但是仍然有个问题：当代码中存在哪怕一个标记不同时，这部分代码你就无法分离出来，这导致了你仍然需要重复大量的代码。比如：

```
# first page

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html lang="en">
<head>
    <title>The current time</title>
</head>
<body>
    <h1>My helpful timestamp site</h1>
    <p>It is now {{ current_date }}.</p>

    <hr>
    <p>Thanks for visiting my site.</p>
</body>
</html>
```
```
# second page

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html lang="en">
<head>
    <title>Future time</title>
</head>
<body>
    <h1>My helpful timestamp site</h1>
    <p>In {{ hour_offset }} hour(s), it will be {{ next_time }}.</p>

    <hr>
    <p>Thanks for visiting my site.</p>
</body>
</html>
```
这两个页面中`<title>`不同，意味着`<title>`以下的部分都不能并入`header.html`中，哪怕下面仍然存在大量的重复代码。所以有了更优雅的解决办法：**extends** -- inculde的逆向思维。


**(2). 我们把模板里面的‘不同代码’进行定义，相同的代码保存为base模板**

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html lang="en">
<head>
    <title>{ block title %}{ endblock %}</title>
</head>
<body>
    <h1>My helpful timestamp site</h1>
    { block content %}{ endblock %}
    { block footer %}
    <hr>
    <p>Thanks for visiting my site.</p>
    { endblock %}
</body>
</html>
```

此时`base.html`变成了一个骨架，你可以把需要的内容填充进去即可，这最大限度实现了代码重用。

```
    # first page

    { extends "base.html" %}

    { block title %}The current time{ endblock %}

    { block content %}
    <p>It is now {{ current_date }}.</p>
    { endblock %}
```

```
    # second page

    { extends "base.html" %}

    { block title %}Future time{ endblock %}

    { block content %}
    <p>In {{ hour_offset }} hour(s), it will be {{ next_time }}.</p>
    { endblock %}
```

woo! 简单优雅！这是Template设计的思想历程。