---
title: Online Hosted Instructions
permalink: index.html
layout: home
---

# RUG Advanced Research Skills 2023 - Week 6 - Session Marcel

Please work through the following lab sessions and try to replicate them as far as possible before the lecture on Oct 10th.

## Lab Sessions to complete as far as po

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| Module | Sub-Lab |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
