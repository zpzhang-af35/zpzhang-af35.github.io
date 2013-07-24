---
layout: page
title: 我是个菜鸟
tagline: But, see me fly ...
---
{% include JB/setup %}

<div class="hero-unit">
  <h1>我真的是个菜鸟</h1>
  <p>很菜很菜的鸟......</p>
</div>

<ul class="posts" id="container" class="js-masonry"
  data-masonry-options='{ "columnWidth": 100, "itemSelector": ".item" }'>
  {% for post in site.posts %}
    <li class='item w2'><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
    <blockquote>{{ post.excerpt }}</blockquote>
    </li>
  {% endfor %}
</ul>