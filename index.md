---
layout: page
title: 寂寞先生
tagline: 这，是一个寂寞的世界……
---
{% include JB/setup %}
---

![thinking](/assets/themes/twitter/img/09140805_ibes.jpg)


人，只是一根会思考的芦苇……



<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a><div>{{ page.excerpt }}</div></li>
  {% endfor %}
</ul>


