---
title: Certificates
---

# Certificates for team 121

<ul>
  {% for file in site.static_files %}
    {% if file.path contains page.dir %}
      <li><a href="{{ file.path }}">{{ file.name }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
