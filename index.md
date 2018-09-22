layout: default.liquid
published_date: 2018-09-17 00:00:00 +0000
title: Tim Schubert
data:
  route: about
---

## Blog

| | |
|:-|:-|{% for post in collections.posts.pages %}{% if post.title != "Articles" %}
| {{ post.published_date | date: "%Y-%m-%d" }} |  [{{ post.title }}](/{{ post.permalink }}) |{% endif %}{% endfor %} 

## Contact

- [Mail](mailto:{{ site.data.contact.mail }})
- [Matrix]({{ site.data.contact.matrix }})
- [Mastodon]({{ site.data.contact.mastodon }})
- [GitHub](https://github.com/{{ site.data.contact.github }})
- [PGP](assets/{{ site.data.contact.pgp }})
