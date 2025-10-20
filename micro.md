---
layout: page
title: "Microblog"
permalink: /micro/
---
<h2 style="margin-bottom: 2rem;">🪶 Microblog</h2>

<div class="micro-feed">
{% for post in site.micro reversed %}
  <div class="micro-card" style="border:1px solid #ddd; border-radius:10px; padding:1rem; margin-bottom:1.5rem; box-shadow:0 2px 5px rgba(0,0,0,0.05); transition: box-shadow 0.2s;">
    <header style="margin-bottom:0.5rem;">
      <h3 style="margin:0;"><a href="{{ post.url }}" style="text-decoration:none; color:#2c3e50;">{{ post.title }}</a></h3>
      <p style="font-size:0.85em; color:#7f8c8d; margin-top:0.2rem;">{{ post.date | date: "%d %B %Y" }}</p>
    </header>

    <div class="micro-excerpt" style="margin-bottom:0.8rem;">
      {{ post.excerpt }}
    </div>

    <a href="{{ post.url }}" class="micro-comments-btn" style="display:inline-block; padding:0.4rem 0.8rem; background-color:#3498db; color:#fff; border-radius:5px; text-decoration:none; font-weight:bold;">💬 Ver comentarios</a>
  </div>
{% endfor %}
</div>

<!-- Opcional: efecto hover -->
<style>
.micro-card:hover {
  box-shadow: 0 4px 12px rgba(0,0,0,0.12);
}
.micro-card h3 a:hover {
  color: #e67e22;
}
.micro-comments-btn:hover {
  background-color: #2980b9;
}
</style>
