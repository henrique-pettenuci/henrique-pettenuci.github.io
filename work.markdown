---
layout: page
title: Work
permalink: /work/
description: Selected initiatives across platform engineering, SRE, cloud operations and FinOps.
---

This page highlights initiatives I manage or have recently executed across DevOps, SRE, and cloud operations.

<div class="project-grid">
  {%- for project in site.projects -%}
    {%- include project-card.html project=project -%}
  {%- endfor -%}
</div>
