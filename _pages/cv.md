---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
---

## Education

- **B.S. in Computer Science and Engineering**, POSTECH, 2025–present

---

## Blog Post Timeline

{% assign all = "" | split: "" %}
{% for post in site.CSE %}{% assign all = all | push: post %}{% endfor %}
{% for post in site.Art %}{% assign all = all | push: post %}{% endfor %}
{% for post in site.Music %}{% assign all = all | push: post %}{% endfor %}
{% for post in site.Other %}{% assign all = all | push: post %}{% endfor %}
{% assign all = all | sort: "date" | reverse %}
{% assign posts_by_year = all | group_by_exp: "post", "post.date | date: '%Y'" %}

{% for year in posts_by_year %}
### {{ year.name }}

{% for post in year.items %}
<div style="display: flex; margin-bottom: 1em; padding-left: 1em; border-left: 2px solid #ddd;">
  <div style="min-width: 90px; font-size: 0.85em; color: #888;">
    {{ post.date | date: "%b %d" }}
  </div>
  <div>
    <strong><a href="{{ post.url }}">{{ post.title }}</a></strong>
    <span style="background: #e8e8e8; padding: 1px 6px; border-radius: 3px; font-size: 0.75em; margin-left: 4px;">{{ post.collection }}</span>
    {% for tag in post.tags %}
      <span style="background: #dceefb; padding: 1px 6px; border-radius: 3px; font-size: 0.75em; margin-left: 4px;">{{ tag }}</span>
    {% endfor %}
    <br/>
    <span style="font-size: 0.85em; color: #666;">{{ post.excerpt | strip_html | truncatewords: 20 }}</span>
  </div>
</div>
{% endfor %}

{% endfor %}
