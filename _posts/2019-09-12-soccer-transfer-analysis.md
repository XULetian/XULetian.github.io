---
title: "Soccer Transfer Network Analysis"
categories:
  - Data Analysis
header:
  overlay_image: "assets/images/post-soccer.png"
  overlay_filter: 0.2
excerpt: "The purpose of this analysis is to discover if there is any transfer preference among these clubs and leagues, which means a league or soccer club might be more willing to do business with some specific clubs or leagues."
mathjax: "true"
tags:
  - Network Analysis
  - Visualization
  - R
---

#### Introduction

For a soccer club, it is very important to consider the transfers of players during summers and winters. Player transfers will produce a great impact on both the loyalty of players in a team and the development of leagues and clubs.

The purpose of this analysis is to discover if there is any transfer preference among these clubs and leagues, which means a league or soccer club might be more willing to do business with some specific clubs or leagues. Social network analysis methods can offer some approaches, so this project is going to use them to examine the networks and to understand the hidden pattern behind it.

{% capture fig_img %}
![Foo]({{ "/assets/images/soccer.png" | relative_url }})
{% endcapture %}

<figure>
  {{ fig_img | markdownify | remove: "<p>" | remove: "</p>" }}
  <figcaption>Photo from Google.</figcaption>
</figure>

