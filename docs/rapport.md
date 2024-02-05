---
layout: default
order: 1
---

{% assign pages = site.pages | sort: "order" %}

{% for page in pages %}
  {% if page.url != "/feed.xml" and  page.url != "/" and page.url != "/rapport.html" %}

{{- page.content -}}

  {% endif %}

{% endfor %}
 