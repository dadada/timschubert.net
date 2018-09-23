+++
title = "Learning Rust"
draft = true
date = 1980-01-01

[taxonomies]
tags = ["rust", "programming", "language"]
+++

## Blog!

{% for post in collections.posts.pages %}
#### {{post.title}}

[{{ post.title }}]({{ post.permalink }})
{% endfor %}
