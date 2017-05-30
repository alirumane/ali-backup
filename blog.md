---
layout: page
title: Blog
header: Blog
group: navigation
---
{% include JB/setup %}

{% for post in site.posts %}
  {{ post.date | date_to_string }} - <a href="{{ post.url }}">{{ post.title }}</a>
  {{ post.excerpt }}
  <a href="{{ post.url }}">See full post</a>
{% endfor %}
