---
title: ABC 프로젝트
icon: fas fa-folder-open
order: 1
permalink: /abc-project/
---

ABC 프로젝트를 진행하며 정리한 글을 모았습니다.

{% assign abc_posts = site.categories['ABC 프로젝트'] %}
{% if abc_posts.size > 0 %}
<ul>
  {% for post in abc_posts %}
  <li><a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></li>
  {% endfor %}
</ul>
{% else %}
아직 등록된 ABC 프로젝트 글이 없습니다.
{% endif %}
