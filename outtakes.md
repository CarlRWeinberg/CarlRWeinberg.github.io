---
layout: default
permalink: /outtakes/
---
# Blog Posts, Deleted Scenes, and Image Outtakes

{% comment %}
=======================
The chunk "assign rawtags" sorts through the files in the _posts folder and gets a list of tags that have been used.
=======================
{% endcomment %}

{% assign rawtags = "" %}
{% for post in site.posts %}
{% assign ttags = post.tags | join:'|' | append:'|' %}
{% assign rawtags = rawtags | append:ttags %}
{% endfor %}
{% assign rawtags = rawtags | split:'|' | sort %}


{% comment %}
=======================
The chunk "assign tags" cleans the tags, makes sure there are no blank tags, and then neatens up the list for use.
=======================
{% endcomment %}

{% assign tags = "" %}
{% for tag in rawtags %}
<!-- {{ tag }} -->
{% if tag != "" %}
{% if tags == "" %}
{% assign tags = tag | split:'|' %}
{% endif %}
{% unless tags contains tag %}
{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
{% endunless %}
{% endif %}
{% endfor %}


{% comment %}
=======================
The chunk "for tag in tags" sorts through the list of available tags, assigns posts to each appropriate tag, and then prints them all out in sorted order for the web site visitor to see.
=======================
{% endcomment %}

{% for tag in tags %}
<h2 id="{{ tag | slugify }}">{{ tag }}</h2>
<ul class=outtakes>
{% for post in site.posts %}
{% if post.tags contains tag %}
<li>{% if post.image %}<img src="{{ site.url }}{{ post.image }}" alt="{{ post.imagedescription }}">{% endif %}
<h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
<ul><small>{{ post.date | date_to_string }}</small><p>{{ post.excerpt }}</p></ul>
</li>
{% endif %}
{% endfor %}
</ul>
{% endfor %}
