---
layout: default
title: Blog
---

<div class="blog-page">
  <h1>Blog Posts</h1>
  
  <div class="post-list">
    {%- for post in site.posts -%}
    <article class="post-item">
      <h2 class="post-title">
        <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
      </h2>
      <span class="post-date">{{ post.date | date: "%B %-d, %Y" }}</span>
      {%- if post.excerpt -%}
      <p class="post-excerpt">{{ post.excerpt | strip_html | truncatewords: 30 }}</p>
      {%- endif -%}
    </article>
    {%- endfor -%}
  </div>
</div>
