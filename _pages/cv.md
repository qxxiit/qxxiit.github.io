---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
---

## Education

2025-        B.S. Student in Computer Science and Engineering, POSTECH
2022-2025    Seoul High


## Work experience

* Fall 2023: Game Dev (Steam)
  * Seoul High
  * Duties includes: Programming, graphic design, composing original soundtracks, etc
  * Supervisor: The Users

 
## Skills
* CSE
  * Sub-skill
  * Sub-skill
* Art
* Music


## Archive Timeline

{% assign all_posts = site.cse | concat: site.art | concat: site.music | concat: site.other | sort: "date" | reverse %}
{% assign posts_by_year = all_posts | group_by_exp: "post", "post.date | date: '%Y'" %}

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
