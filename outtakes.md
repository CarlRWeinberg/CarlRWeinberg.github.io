---
layout: default
permalink: /outtakes/
---

## Outtakes from Red Dynamite

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>