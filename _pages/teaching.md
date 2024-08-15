---
layout: page
title: teaching
permalink: /teaching/
description: A non-exhaustive list of teaching assignments
nav: true
nav_order: 2
display_categories: [ta, ma, ba, sa]
horizontal: false
---

<!-- pages/teaching.md -->
<div class="teaching">
{%- if site.enable_ta_categories and page.display_categories %}
  <!-- Display categorized teaching -->
  {%- for category in page.display_categories %}
  <h2 class="category">{{ category }}</h2>
  {%- assign categorized_ta = site.teaching | where: "category", category -%}
  {%- assign sorted_ta = categorized_ta | sort: "importance" %}
  <!-- Generate cards for each teaching -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for teaching in sorted_ta -%}
      {% include ta_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for teaching in sorted_ta -%}
      {% include teaching.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
  {% endfor %}

{%- else -%}
<!-- Display teaching without categories -->
  {%- assign sorted_ta = site.teaching | sort: "importance" -%}
  <!-- Generate cards for each teaching -->
  {% if page.horizontal -%}
  <div class="container">
    <div class="row row-cols-2">
    {%- for teaching in sorted_ta -%}
      {% include ta_horizontal.html %}
    {%- endfor %}
    </div>
  </div>
  {%- else -%}
  <div class="grid">
    {%- for teaching in sorted_ta -%}
      {% include teaching.html %}
    {%- endfor %}
  </div>
  {%- endif -%}
{%- endif -%}
</div>
