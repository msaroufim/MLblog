---
title: First Post
layout: default
---
# Math, Machine Learning & Programming fugues (Obviously not design)



---
---

{% for post in site.posts limit: 10 %}
<div class="row-fluid">
  <div class="span12">
    <h2>{{ post.title }}</h2>
    <h5>{{ post.date | date_to_long_string }}</h5>
    <br>
    <p>
      {{post.content | strip_html | truncatewords:75}}<br>
      <a href="{{ post.url }}">Read More</a>
    </p>
  </div>
</div>
---
{% endfor %}