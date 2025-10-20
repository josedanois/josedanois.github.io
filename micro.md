---
layout: page
title: "Microblog"
permalink: /micro/
---

<h2>🪶 Microblog</h2>

{% for post in site.micro reversed %}
  <article class="micro-entry">
    <h3>{{ post.title }}</h3>
    <div class="micro-content">
      {{ post.content }}
    </div>
    <p class="micro-date">{{ post.date | date: "%d %B %Y" }}</p>

    <!-- Bloque individual de comentarios -->
    <div id="graphcomment-{{ forloop.index }}"></div>
    <script type="text/javascript">
      (function() {
        var gc_div = document.getElementById("graphcomment-{{ forloop.index }}");
        var gc_params = {
          graphcomment_id: "josedanois",
          page_id: "{{ post.url }}",
          fixed_header_height: 0
        };
        var s = document.createElement('script');
        s.type = 'text/javascript';
        s.async = true;
        s.src = 'https://graphcomment.com/js/integration.js?' + Date.now();
        s.onload = function() { window.gc_params = gc_params; };
        gc_div.appendChild(s);
      })();
    </script>

    <hr>
  </article>
{% endfor %}
