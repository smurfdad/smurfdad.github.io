---
layout: resumen
title: Categorias
permalink: /categorias/index.html
---
{% assign rawtags = "" %}
{% for post in site.posts %}
  {% assign ttags = post.categories | join:'|' | append:'|' %}
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
    <li><a href="#{{ tag | slugify }}"> {{ tag | capitalize}} </a></li>
  {% endfor %}
</ul>
{% for tag in tags %}
  <div class="bs-callout bs-callout-success text-justify" id="{{ tag | slugify }}">
  <h3>{{ tag | capitalize}}</h3>
  <ul class="list-unstyled">
    {% for post in site.posts %}
      {% if post.categories contains tag %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
      {% endif %}
    {% endfor %}
  </ul>
  </div>
{% endfor %}