---
layout: page
title: Blog
header: Blog
group: navigation
---

{% include JB/setup %}

{% for post in site.posts %}

{{ post.date | date_to_string }} - {{ post.title }}
{{ post.excerpt }} See full post
{% endfor %}
