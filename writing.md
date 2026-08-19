---
layout: page
title: Writing
permalink: /writing/
---

{% if site.posts.size > 0 %}
{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }}) — {{ post.date | date: "%B %-d, %Y" }}
{% endfor %}
{% else %}
There are no published articles in the collection.
{% endif %}
