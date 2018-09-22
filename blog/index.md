layout: default.liquid 
title: Articles
published_date: 2018-09-17 00:00:00 +0000
data:
  route: blog
---

# {{ page.title }}

| | |
|:-|:-|{% for post in collections.posts.pages %}{% if post.title != "Articles" %}
| {{ post.published_date | date: "%Y-%m-%d" }} |  [{{ post.title }}](/{{ post.permalink }}) |{% endif %}{% endfor %} 
