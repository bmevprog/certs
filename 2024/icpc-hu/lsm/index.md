---
title: Certificates for team LSM
---

# Certificates for team LSM

<ul>
  {%- assign folders = "" | split: "" -%}
  {%- assign files   = "" | split: "" -%}

  {%- for file in site.static_files -%}
    {%- assign rel = file.path | remove_first: page.dir -%}
    {%- if rel != file.path -%}
      {%- assign parts = rel | split: "/" -%}
      {%- if parts.size > 1 -%}
        {%- assign folder = parts[0] -%}
        {%- unless folder == "" or folders contains folder -%}
          {%- assign folders = folders | push: folder -%}
        {%- endunless -%}
      {%- else -%}
        {%- assign filename = parts[0] -%}
        {%- unless filename == "" or filename == page.name or files contains filename -%}
          {%- assign files = files | push: filename -%}
        {%- endunless -%}
      {%- endif -%}
    {%- endif -%}
  {%- endfor -%}

  {%- assign folders = folders | sort -%}
  {%- assign files   = files   | sort -%}

  {%- for d in folders -%}
    <li>📁 <a href="{{ (page.dir | append: d | append: '/') | relative_url }}">{{ d }}/</a></li>
  {%- endfor -%}

  {%- for f in files -%}
    <li>📄 <a href="{{ (page.dir | append: f) | relative_url }}">{{ f }}</a></li>
  {%- endfor -%}
</ul>
