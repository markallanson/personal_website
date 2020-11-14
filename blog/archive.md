---
id: -3
title: Post Archive
date: 2012-08-11T18:55:26+00:00
author: Mark
layout: default
guid: archive
---
{% for post in site.posts %}
{% capture current_year %}{{ post.date | date: "%Y" }}{% endcapture %}
{% if current_year != previous_year %}
### {{ post.date | date: '%Y' }}
{% endif %}
   * [{{ post.title}}]({{ post.url }})
{% assign previous_year = current_year %}
{% endfor %}
