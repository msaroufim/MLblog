---
title: First Post
layout: default
---




{% for post in site.posts limit: 10 %}
<div class="row-fluid">
  <div class="span12">
    <a href="{{post.url}}"><h3>{{ post.title }}</h3></a>
    {{ post.date | date_to_long_string }}
    <br>
    <br>
    <p>
      {{post.content | strip_html | truncatewords:75}}<br>
      <a href="{{ post.url }}">Read More</a>
    </p>
  </div>
</div>
---
{% endfor %}
