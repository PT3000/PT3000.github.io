---
title: 알고리즘
icon: fas fa-code
order: 0
permalink: /algorithms/
---

알고리즘 문제 풀이와 개념 정리를 풀이 사이트별로 모았다.

## 백준

{% assign boj_posts = site.categories['백준'] %}
{% if boj_posts.size > 0 %}
<ul>
  {% for post in boj_posts %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
{% else %}
아직 등록된 백준 글이 없다.
{% endif %}

## 프로그래머스

{% assign programmers_posts = site.categories['프로그래머스'] %}
{% if programmers_posts.size > 0 %}
<ul>
  {% for post in programmers_posts %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
{% else %}
아직 등록된 프로그래머스 글이 없다.
{% endif %}
