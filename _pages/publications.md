---
title: "Publications"
permalink: /publications/
---

# Publications

Below is a list of my publications.

{% for pub in site.publications %}
- [{{ pub.title }}]({{ pub.url }}) — *{{ pub.venue }}*, {{ pub.year }}
{% endfor %}
