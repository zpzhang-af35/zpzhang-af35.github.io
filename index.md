---
layout: page
title: Hello World!
tagline: Supporting tagline
---
{% include JB/setup %}

<ul class="posts js-masonry" id="container" data-masonry-options='{ "columnWidth": 100, "itemSelector": ".item" }'>
  {% for post in site.posts %}
    <li class='item w2'><span>{{ post.date | date_to_string }}</span> &raquo; 
    <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
    <blockquote>{{ post.excerpt }}</blockquote>
    </li>
  {% endfor %}
</ul>
