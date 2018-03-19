---
layout: post
title:  "Jekyll Setup!"
date:   2018-03-20 01:38:49 +0800
categories: jekyll update
---
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

