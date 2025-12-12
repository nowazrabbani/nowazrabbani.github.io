---
layout: default
title: "Publications"
nav_order: 4
permalink: /publications/
---

# Publications

{% for pub in site.publications %}
- [{{ pub.title }}]({{ pub.url }}) — {{ pub.year }}, {{ pub.venue }}
{% endfor %}
