---
layout: page
title: ta
permalink: /ta/
description: A non-exhaustive list of TA 
nav: true
nav_order: 2
display_categories: [ethz, epfl]
horizontal: false
---

<!-- pages/ta.md -->
<div class="ta">
{%- if site.enable_ta_categories and page.display_categories %}
  <!-- Display categorized ta -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_ta = site.ta | where: "category", category -%}
  {%- assign sorted_ta = categorized_ta | sort: "importance" %}
  <!-- Generate cards for each ta -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for ta in sorted_ta -%}
      {% include ta_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for ta in sorted_ta -%}
      {% include ta.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display ta without categories -->
  {%- assign sorted_ta = site.ta | sort: "importance" -%}
  <!-- Generate cards for each ta -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for ta in sorted_ta -%}
      {% include ta_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for ta in sorted_ta -%}
      {% include ta.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
