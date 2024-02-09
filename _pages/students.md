---
layout: page
permalink: /students/
title: students
description: Amazing work of the students I supervised. Some there are some joint dissertations done by more than one student.
nav_order: 5
---
<!-- _pages/students.md -->
<div class="publications">

{%- for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f students -q @*[year={{y}}]* %}
{% endfor %}

</div>
