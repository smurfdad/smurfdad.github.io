---
layout: resumen
title: Ingredientes
permalink: /tags/index.html
---

{% comment%}
Here we generate all the tags.
{% endcomment%}

{% assign rawtags = "" %}
{% for post in site.posts %}
{% assign ttags = post.tags | join:'|' | append:'|' %}
{% assign rawtags = rawtags | append:ttags %}
{% endfor %}

{% assign rawtags = rawtags | split:'|' | sort %}

{% assign tags = "" %}

{% for tag in rawtags %}
{% if tag != "" %}

{% if tags == "" %}
{% assign tags = tag | split:'|' %}
{% endif %}

{% unless tags contains tag %}
{% assign tags = tags | join:'|' | append:'|' | append:tag | split:'|' %}
{% endunless %}
{% endif %}
{% endfor %}

<ul class="list-inline">
{% for tag in tags %}
<li><a href="#{{ tag | slugify }}"> {{ tag | capitalize}} </a> &nbsp;&nbsp;</li>
{% endfor %}
</ul>

{% for tag in tags %}
<div class="bs-callout bs-callout-info text-justify" id="{{ tag | slugify }}">
<h3>{{ tag | capitalize }}</h3>
<ul class="list-unstyled">
  {% for post in site.posts %}
    {% if post.tags contains tag %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endif %}
  {% endfor %}
</ul>
</div>
{% endfor %}