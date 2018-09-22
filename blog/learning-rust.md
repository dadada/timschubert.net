layout: blogpost.liquid
title: Learning Rust
is_draft: true
data:
  route: blog
---
## Blog!

{% for post in collections.posts.pages %}
#### {{post.title}}

[{{ post.title }}]({{ post.permalink }})
{% endfor %}
