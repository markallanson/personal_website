---
id: -1
author: Mark
layout: default
guid: blog-index
---
{% for post in site.posts limit:3 %}

## [{{ post.title }}]({{ post.url }})
[{{ post.date | date: "%B %-d, %Y" }}]({{ post.url }})

{{ post.content }}

---

{% endfor %}

[Post Archive](archive.html)