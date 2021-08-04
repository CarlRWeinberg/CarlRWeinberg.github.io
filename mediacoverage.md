---
layout: default
permalink: /mediacoverage/
---

## Media Coverage of Red Dynamite

<ul>
{% assign SortedList = site.data.mediacoverage | sort: "date" %}
{% for item in SortedList %}<li>{{ item.pubdate | date: "%a, %b %d, %y" }}: {% if item.url %}<a href="{{ item.url }}" target="_blank">{% endif %}{{ item.title }}{% if item.url %}</a>{% endif %}{% if item.publication %}<em>({{item.publication}})</em>{% endif %}{% if item.synopsis %}<ul>{{item.synopsis}}</ul>{% endif %}{% endfor %}
</ul>
