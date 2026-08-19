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
Writing will appear here soon. In the meantime, see what I am
[reading]({{ "/reading/" | relative_url }}).
{% endif %}
