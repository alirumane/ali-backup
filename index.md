---
layout: index
title: Home
tagline: HomePage
---
{% include JB/setup %}

{% for post in site.posts %}
  <div class="panel panel-default">
    <div class="panel-heading">
    {{ post.date | date_to_string }} - <a href="{{ post.url }}">{{ post.title }}</a></div>
    <div class="panel-body">
      {{ post.description | truncate: 150 }}
      <a href="{{ post.url }}">See full post</a>
    </div>
  </div>
{% endfor %}
