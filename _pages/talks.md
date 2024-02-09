---
layout: page
permalink: /talks/
title: talks
description: talks by categories in reversed chronological order.
nav_order: 4
---
<!-- _pages/talks.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f talks -q @*[year={{y}}]* %}
{% endfor %}

</div>
