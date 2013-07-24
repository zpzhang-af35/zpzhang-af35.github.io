---
layout: page
title: See me fly
tagline: I am singing in the sky
---
{% include JB/setup %}

<div class="hero-unit">
  <h1>我真的是个菜鸟</h1>
  <p>很菜很菜的鸟......</p>
</div>

<ul class="posts js-masonry" id="container" data-masonry-options='{ "columnWidth": 100, "itemSelector": ".item" }'>
  {% for post in site.posts %}
  
    <li class='item'>
    <h3><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h3>
    <h4>{{ post.date | date_to_string }}</h4>
    <blockquote>{{ post.excerpt }}</blockquote>
    </li>
  {% endfor %}
</ul>
