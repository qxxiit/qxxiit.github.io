---
permalink: /
title: "Home"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

Welcome to the archive.

## Recent posts

{% assign all_posts = site.CSE | concat: site.Art | concat: site.Music | concat: site.Other | sort: "date" | reverse %}

{% for post in all_posts limit: 10 %}
<div style="margin-bottom: 1.5em;">
  <h3 style="margin-bottom: 0.2em;">
    <a href="{{ post.url }}">{{ post.title }}</a>
  </h3>
  <p style="font-size: 0.85em; color: #666; margin: 0.2em 0;">
    {{ post.date | date: "%B %d, %Y" }}
    <span style="background: #e8e8e8; padding: 2px 8px; border-radius: 4px; font-size: 0.8em; margin-left: 4px;">{{ post.collection }}</span>
  </p>
  <p>{{ post.excerpt | strip_html | truncatewords: 40 }}</p>
</div>
{% endfor %}
