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

{% assign all = "" | split: "" %}
{% for post in site.CSE %}{% assign all = all | push: post %}{% endfor %}
{% for post in site.Art %}{% assign all = all | push: post %}{% endfor %}
{% for post in site.Music %}{% assign all = all | push: post %}{% endfor %}
{% for post in site.Other %}{% assign all = all | push: post %}{% endfor %}
{% assign all = all | sort: "date" | reverse %}

{% for post in all limit:10 %}
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
