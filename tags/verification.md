---
layout: page
title: "Tag: Verification"
permalink: /tags/verification/
---

Verification is the discipline of checking claims against external evidence so disagreement can converge.

Related tags: [epistemology](/tags/epistemology/), [shared-reality](/tags/shared-reality/), [media-systems](/tags/media-systems/).

{% assign posts = site.tags['verification'] %}
{% if posts %}
{% for post in posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
{% else %}
No essays tagged yet.
{% endif %}
