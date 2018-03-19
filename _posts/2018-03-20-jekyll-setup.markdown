---
layout: post
title:  "Jekyll Setup!"
date:   2018-03-20 01:38:49 +0800
categories: jekyll update
---
Reference:
1. [Jekyll quickstart guide][jekyll guide]
2. [Use github to serve jekyll][serve jekyll]

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

[jekyll guide]: https://jekyllrb.com/docs/quickstart/
[serve jekyll]: https://www.sylvaindurand.org/using-github-to-serve-jekyll/
