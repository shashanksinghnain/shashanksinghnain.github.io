---
layout: page
permalink: /research/
title: research
description:
nav: true
nav_order: 1
---
<!-- _pages/publications.md -->
<div class="publications">

<h2 class="bibliography">Pre-PhD Research</h2>
{% bibliography -f papers --query @*[year=2025]* %}

<h2 class="bibliography">Undergraduate Research</h2>
{% bibliography -f papers --query @*[year=2023]* %}

</div>
