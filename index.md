---
layout: default
title: Home
---

<div class="hero">
  <img src="{{ '/assets/logos/svg/logo-lockup.svg' | relative_url }}" alt="VDI logo">
  <h1>Virtual Data Infrastructure</h1>
  <p>A shared platform for managing virtual data resources.</p>
</div>

## Repositories

<ul class="repo-list">
  {% for repo in site.data.repos %}
  <li>
    <a href="{{ repo.url }}">{{ repo.name }}</a>
    <p>{{ repo.description }}</p>
  </li>
  {% endfor %}
</ul>

<p class="coming-soon">More content will be added here in the future.</p>
