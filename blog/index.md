layout: page.liquid
title: index
published_date: 2018-09-17 00:00:00 +0000
data:
  route: "blog"
---

| | |
|:-|:-|{% for post in collections.posts.pages %}{% if post.title != "index" %}
| {{ post.published_date | date: "%Y-%m-%d" }} |  [{{ post.title }}](/{{ post.permalink }}) |{% endif %}{% endfor %} 
