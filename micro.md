---
layout: page
title: Microblog
permalink: /micro/
---

<h2>Microblog</h2>

<ul>
{% for post in site.micro reversed %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a> – <small>{{ post.date | date: "%b %-d, %Y" }}</small>
    <p>{{ post.content | strip_html | truncatewords: 25 }}</p>
  </li>
{% endfor %}
</ul>
