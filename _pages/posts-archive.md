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

{% include feature_row id="intro" type="center" %}

{% include feature_row %}

{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="right" %}

{% include feature_row id="feature_row4" type="center" %}