---
title: Blog
layout: wikistyle
---

Blog
====

{% for post in site.posts limit: 100 %}
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <h3 class="datetext" style="float:left">
    Posted on {{ post.date | date_to_string }}

  </h3>
 <span style="float:right"><a class="comments" data-disqus-identifier="{{ post.disqus_id }}" href="{{ post.url }}#disqus_thread">View Comments</a></span>

<div class="c">&nbsp;</div>
  <p>{{ post.content | strip_html | truncatewords: 75 }}</p>
  <p><a href="{{ post.url }}">Read more...</a></p>
{% endfor %}