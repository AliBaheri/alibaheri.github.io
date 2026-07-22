---
layout: page
permalink: /publications/
title: publications
description: Publications since 2023, in reversed chronological order. For the complete list, see my <a href="https://scholar.google.com/citations?user=MhIEockAAAAJ" target="_blank">Google Scholar</a> profile or <a href="/assets/pdf/cv_academic.pdf" target="_blank">CV</a>.
years: [2026, 2025, 2024, 2023]
nav: true
---

<div class="publications">

{% for y in page.years %}
  <h2 class="year">{{y}}</h2>
  {% bibliography -f papers -q @*[year={{y}}]* %}
{% endfor %}

</div>
