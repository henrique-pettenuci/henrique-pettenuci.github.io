---
layout: page
title: Projects
permalink: /projects/
---

This page highlights initiatives I manage or have recently executed across DevOps, SRE, and cloud operations.

<div class="project-grid">
  {%- for project in site.projects -%}
    {%- include project-card.html project=project -%}
  {%- endfor -%}
</div>
