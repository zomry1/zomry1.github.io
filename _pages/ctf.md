---
layout: page
title: CTF
permalink: /ctf/
---

{% for posty in site.posts %}
  {% if posty.ctf %}
  <li>
  <a href="{{ posty.url }}">{{posty.title}}</a>
  </li>
  <hr>
  {% endif %}
{% endfor %}