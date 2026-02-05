---
layout: page
title: "Tag: Media Systems"
permalink: /tags/media-systems/
---

Media systems examine how information is selected, amplified, and distorted by institutions and platforms.

Related tags: [attention-economy](/tags/attention-economy/), [amplification](/tags/amplification/), [public-discourse](/tags/public-discourse/).

{% assign posts = site.tags['media-systems'] %}
{% if posts %}
{% for post in posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
{% else %}
No essays tagged yet.
{% endif %}
