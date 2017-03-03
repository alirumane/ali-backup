---
layout: default
title: Ali Rumane
tagline: I use light weight heavy impact yools for my work
---

{% for post in site.posts %}
  <div class="panel panel-default">
    <div class="panel-heading">
    {{ post.date | date_to_string }} - <a href="{{ post.url }}">{{ post.title }}</a></div>
    <div class="panel-body">
      {{ post.excerpt }}
      <a href="{{ post.url }}">See full post</a>
    </div>
  </div>
{% endfor %}
