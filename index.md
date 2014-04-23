---
layout: page
title: 寂寞先生
tagline: 这，是一个寂寞的世界……
---
{% include JB/setup %}
# 人，只是一根会思考的芦苇……
---


{% for post in site.posts %}
<div class = "card">
	<div class = "clearfix">
		<span  class = "date_label">{{ post.date | date:"%m-%d %Y" }}</span> 
	</div>
		{{ post.content  | | split:'<!--break-->' | first }}
	<div class = "read_more">
		<a href="{{ BASE_PATH }}{{ post.url }}">&hellip;查看全文</a>
	</div>
	
</div>
<hr>
{% endfor %}



