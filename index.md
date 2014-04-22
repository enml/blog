---
layout: page
title: 寂寞先生
tagline: 这，是一个寂寞的世界……
---
{% include JB/setup %}
---

![thinking](http://pic7.nipic.com/20100429/1627833_113530061821_2.jpg)


那是我吗？不，



<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a><div>{{ page.excerpt }}</div></li>
  {% endfor %}
</ul>


