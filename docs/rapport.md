---
layout: default
slug: /index
order: 1
---

{% assign chapitres = site.pages | sort: "order" %}

{% for chapitre in chapitres %}
  {% if chapitre.title %}
    {{ chapitre.content }}
  {% endif %}
{% endfor %}

 