---
layout: page
title: "Microblog"
permalink: /micro/
---

<h2>Microblog</h2>
<p class="micro-intro">Reflexiones cortas, pensamientos y notas rápidas del día.</p>

<div class="micro-timeline">
  {% for post in site.micro reversed %}
    <div class="micro-item">
      <div class="micro-date">{{ post.date | date: "%d %b %Y" }}</div>
      <div class="micro-text">{{ post.content | markdownify }}</div>
    </div>
  {% endfor %}
</div>

