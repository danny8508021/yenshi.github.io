---
layout: default
title: English Posts
posts_name:
  en: English
  tw: 英文
lang: en
permalink: /en/posts/
---

<div class="home">

  {%- if site.posts.size > 0 -%}
    <h2 class="post-list-heading">{{ page.title }}</h2>
    <ul class="post-list">
      {%- for post in site.posts -%}
      {%- if post.lang == page.lang -%}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {%- if site.show_excerpts -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
      {%- endif -%}
      {%- endfor -%}
    </ul>

  {%- endif -%}

</div>
