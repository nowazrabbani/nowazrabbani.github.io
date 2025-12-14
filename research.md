---
layout: default
title: "Research"
nav_order: 2
permalink: /research/
---

# Research

Below are selected research projects:

{% for project in site.projects %}
- [{{ project.title }}]({{ project.url }})
{% endfor %}
