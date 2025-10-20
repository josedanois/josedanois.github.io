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

  <!-- 🔹 Bloque individual de comentarios GraphComment -->
  <div id="graphcomment-{{ forloop.index }}"></div>
  <script type="text/javascript">
    (function() {
      var divId = "graphcomment-{{ forloop.index }}";
      var gc_div = document.getElementById(divId);
      if (!gc_div) return;

      // Cada entrada usa su propia URL como identificador de hilo
      window["gc_params_" + divId] = {
        graphcomment_id: "josedanois", // 👈 tu GraphComment ID
        page_id: "{{ post.url }}",
        fixed_header_height: 0
      };

      var s = document.createElement('script');
      s.type = 'text/javascript';
      s.async = true;
      s.src = 'https://graphcomment.com/js/integration.js?' + Date.now();
      s.onload = function() { window.gc_params = window["gc_params_" + divId]; };
      gc_div.appendChild(s);
    })();
  </script>
</article>
{% endfor %}
