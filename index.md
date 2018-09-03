layout: page.liquid
title: Tim Schubert
---

## Contact

- [Mail](mailto:{{ site.data.contact.mail }})
- [ActivityPub]({{ site.data.contact.mastodon }})
- [Matrix]({{ site.data.contact.matrix }})
- [GitHub](https://github.com/{{ site.data.contact.github }})
- [PGP](assets/{{ site.data.contact.pgp }})

## Blog

{% for post in collections.posts.pages %}
- [{{ post.published_date | date: "%Y-%m-%d" }} {{ post.title }}]({{ post.permalink }}){% endfor %}
