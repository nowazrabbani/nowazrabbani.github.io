---
layout: default
title: "Publications"
nav_order: 3
permalink: /publications/
---

# Publications

{% for pub in site.publications %}
- [{{ pub.title }}]({{ pub.url }}) — {{ pub.year }}, {{ pub.venue }}
{% endfor %}
