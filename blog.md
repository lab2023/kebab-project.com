---
title: Blog
layout: wikistyle
---

Blog
====

{% for post in site.posts  %}

<h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
{{ post.date | date_to_string }}
<p>{{ post.content | strip_html | truncatewords: 75 }}</p>
<p><a href="{{ post.url }}">Read more...</a></p>

{% endfor %}