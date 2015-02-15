---
title: First Post
layout: default
---
# ++++++++[>++++[>++>+++>+++>+<<<<-]>+>+>->>+[<]<-]>>.>---.+++++++..+++.>>.<-.<.+++.------.--------.>>+.>++.



Hey Everyone, welcome to my blog. I'll be posting things that I think are cool, this will include summarizing cool machine learning or theoretical computer science results and when applicable an in browser demo of the results. Sometimes I'll also post my personal opinions on tech and philosophy. I'm still learning how Jekyll works so I hope that the aesthetics of this blog will improve over time.

{% for post in site.posts limit: 10 %}
<div class="row-fluid">
  <div class="span12">
    <h2>{{ post.title }}</h2>
    <h4>{{ post.date | date_to_long_string }}</h4>
    <p>
      {{post.content | strip_html | truncatewords:75}}<br>
      <a href="{{ post.url }}">Read More</a>
    </p>
  </div>
</div>
{% endfor %}