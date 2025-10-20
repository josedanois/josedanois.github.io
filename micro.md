---
layout: page
title: "Microblog"
permalink: /micro/
---

<h2>Microblog</h2>
<p class="micro-intro">Reflexiones cortas, pensamientos y notas rápidas del día.</p>

<div class="micro-timeline">
 {% for post in site.micro reversed %}
<article class="micro-entry" style="margin-bottom: 3rem; border-bottom: 1px solid #ddd; padding-bottom: 1.5rem;">
  <header>
    <h3 style="margin-bottom: 0.3rem;">{{ post.title }}</h3>
    <p class="text-muted" style="font-size: 0.9em;">{{ post.date | date: "%d %B %Y" }}</p>
  </header>

  <div class="micro-content" style="margin-bottom: 1rem;">
    {{ post.content }}
  </div>

  <!-- 🔹 Botón para cargar comentarios -->
  <button class="load-comments-btn" 
          data-post-id="{{ post.url | slugify }}" 
          data-post-url="{{ post.url }}" 
          style="background-color:#f2f2f2; border:1px solid #ccc; border-radius:6px; padding:0.4rem 0.8rem; cursor:pointer;">
    💬 Ver comentarios
  </button>

  <div id="graphcomment-{{ post.url | slugify }}" style="margin-top: 1rem;"></div>
</article>
{% endfor %}

<!-- 🔹 Script global para carga diferida -->
<script type="text/javascript">
document.addEventListener('DOMContentLoaded', function() {
  const buttons = document.querySelectorAll('.load-comments-btn');
  buttons.forEach(function(btn) {
    btn.addEventListener('click', function() {
      const postId = btn.dataset.postId;
      const postUrl = btn.dataset.postUrl;
      const container = document.getElementById('graphcomment-' + postId);

      if (container.innerHTML.trim() !== '') return; // ya cargado

      // Configura los parámetros de GraphComment para este post
      window["gc_params_" + postId] = {
        graphcomment_id: "jdanois", // 👈 tu GraphComment ID
        page_id: postUrl,
        fixed_header_height: 0
      };

      const s = document.createElement('script');
      s.type = 'text/javascript';
      s.async = true;
      s.src = 'https://graphcomment.com/js/integration.js?' + Date.now();
      s.onload = function() { window.gc_params = window["gc_params_" + postId]; };
      container.appendChild(s);

      // Cambia el texto del botón
      btn.textContent = "💬 Comentarios cargados";
      btn.disabled = true;
      btn.style.opacity = "0.7";
    });
  });
});
</script>
