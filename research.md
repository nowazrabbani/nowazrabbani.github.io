---
title: "Research"
permalink: /research/
---

# Research

Here are selected research projects. Each project page includes problem motivation, approach, theoretical results, and experimental outcomes.

{% for project in site.projects %}
- [{{ project.title }}]({{ project.url }})
{% endfor %}
