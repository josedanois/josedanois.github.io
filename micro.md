---
layout: page
title: "Microblog"
permalink: /micro/
---

<h2 style="margin-bottom:2rem;">🪶 Microblog</h2>

<div class="micro-timeline" style="position:relative; margin-left:1.5rem; padding-left:1rem; border-left:2px solid #3498db;">
{% for post in site.micro reversed %}
  <div class="micro-item" style="position:relative; margin-bottom:2rem;">
    <!-- Marcador de fecha a la izquierda -->
    <div class="micro-date" style="position:absolute; left:-3.5rem; top:0; width:3rem; text-align:right; font-size:0.8em; color:#7f8c8d;">
      {{ post.date | date: "%d %b %Y" }}
    </div>

    <!-- Tarjeta del post -->
    <div class="micro-card" style="border:1px solid #ddd; border-radius:10px; padding:1rem; box-shadow:0 2px 5px rgba(0,0,0,0.05); transition: box-shadow 0.2s;">
      <h3 style="margin:0 0 0.3rem 0;"><a href="{{ post.url }}" style="text-decoration:none; color:#2c3e50;">{{ post.title }}</a></h3>
      <div class="micro-excerpt" style="margin-bottom:0.5rem;">
        {{ post.excerpt }}
      </div>
      <a href="{{ post.url }}" class="micro-comments-btn" style="display:inline-block; padding:0.4rem 0.8rem; background-color:#3498db; color:#fff; border-radius:5px; text-decoration:none; font-weight:bold;">💬 Ver comentarios</a>
    </div>
  </div>
{% endfor %}
</div>

<!-- Estilos hover -->
<style>
.micro-card:hover {
  box-shadow:0 4px 12px rgba(0,0,0,0.12);
}
.micro-card h3 a:hover {
  color:#e67e22;
}
.micro-comments-btn:hover {
  background-color:#2980b9;
}
@media(max-width:600px){
  .micro-date {
    position: static;
    text-align:left;
    margin-bottom:0.3rem;
  }
  .micro-timeline {
    margin-left:0;
    padding-left:0;
    border-left:none;
  }
}
</style>
