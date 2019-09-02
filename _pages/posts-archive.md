---
layout: archive
permalink: /posts/
title: "All posts"
author_profile: true
header:
  image: "assets/images/post.png"
---
{% for post in site.posts limit: 10 %}
  {% include archive-single.html %}
{% endfor %}
