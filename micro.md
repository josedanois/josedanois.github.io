---
layout: page
title: "Microblog"
permalink: /micro/
---

<h2 style="margin-bottom:2rem; text-align:center;">🪶 Microblog</h2>

<div class="micro-feed">
{% assign colors = "#3498db,#e67e22,#2ecc71,#9b59b6,#f39c12,#1abc9c,#e74c3c,#34495e" | split: "," %}
{% for post in site.micro reversed %}
  <div class="micro-card">
    <!-- Cabecera -->
    <header>
      <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
      <p class="micro-date">{{ post.date | date: "%d %B %Y" }}</p>
    </header>

    <!-- Contenido resumido -->
    <div class="micro-excerpt">
      {{ post.excerpt }}
    </div>

    <!-- Etiquetas / hashtags con iconos -->
    {% if post.tags %}
    <div class="micro-tags">
      {% for tag in post.tags %}
        {% assign color_index = forloop.index0 | modulo: colors.size %}
        <span class="micro-tag" style="background-color:{{ colors[color_index] }}">
          🔹 #{{ tag }}
        </span>
      {% endfor %}
    </div>
    {% endif %}

    <!-- Botón comentarios -->
    <a href="{{ post.url }}" class="micro-comments-btn">💬 Ver comentarios</a>
  </div>
{% endfor %}
</div>

<!-- Estilos CSS -->
<style>
.micro-feed {
  max-width: 700px;
  margin: 0 auto;
}
.micro-card {
  border:1px solid #ddd;
  border-radius:12px;
  padding:1rem;
  margin-bottom:1.5rem;
  box-shadow:0 2px 8px rgba(0,0,0,0.05);
  transition: all 0.3s ease;
}
.micro-card:hover {
  box-shadow:0 6px 18px rgba(0,0,0,0.15);
  transform: translateY(-2px);
}
.micro-card h3 a {
  text-decoration:none;
  color:#2c3e50;
  transition: color 0.2s;
}
.micro-card h3 a:hover {
  color:#e67e22;
}
.micro-date {
  font-size:0.85em;
  color:#7f8c8d;
  margin-top:0.2rem;
}
.micro-excerpt {
  margin:0.5rem 0;
  line-height:1.5;
  color:#2c3e50;
}
.micro-tags {
  margin-bottom:0.5rem;
}
.micro-tag {
  display:inline-block;
  padding:0.2rem 0.6rem;
  border-radius:5px;
  font-size:0.8em;
  color:#fff;
  margin-right:0.3rem;
  margin-bottom:0.3rem;
  transition: transform 0.2s, box-shadow 0.2s;
  cursor:default;
}
.micro-tag:hover {
  transform: translateY(-2px);
  box-shadow:0 2px 6px rgba(0,0,0,0.15);
}
.micro-comments-btn {
  display:inline-block;
  padding:0.4rem 0.8rem;
  background-color:#3498db;
  color:#fff;
  border-radius:6px;
  text-decoration:none;
  font-weight:bold;
  transition: background-color 0.2s, transform 0.2s;
}
.micro-comments-btn:hover {
  background-color:#2980b9;
  transform: translateY(-1px);
}
@media(max-width:600px){
  .micro-card {
    padding:0.8rem;
  }
  .micro-tags {
    display:flex;
    flex-wrap:wrap;
  }
}
</style>

