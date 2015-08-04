---
title: First Post
layout: default
---




{% for post in site.posts limit: 10 %}
<div class="row-fluid">
  <div class="span12">
    <a href="{{post.url}}"><h2>{{ post.title }}</h2></a>
    <h5>{{ post.date | date_to_long_string }}</h5>
    
    <p>
      {{post.content | strip_html | truncatewords:75}}<br>
      <a href="{{ post.url }}">Read More</a>
    </p>
  </div>
</div>
---
{% endfor %}
