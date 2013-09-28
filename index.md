---
layout: page
title: 首页
tagline: natural language processing | machine translation | machine learning | algorithms | coding
---
{% include JB/setup %}

## elephantgcc|大象无形

I read I forget, I write I remember, I do I understand.

上士闻道，勤而行之；中士闻道，若存若亡；下士为道，大笑之。不笑，不足以为道。  —— 老子《道德经》



## 文章列表

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> >>  <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>


![xxx]({{ site.url }}/assets/qrcode.png)

