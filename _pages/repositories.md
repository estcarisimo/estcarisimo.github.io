---
layout: page
permalink: /repositories/
title: tools
description: Tools and Repositories
nav: true
nav_order: 4
---

{% if site.data.repositories.github_users %}

## GitHub users

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for user in site.data.repositories.github_users %}
    {% include repository/repo_user.liquid username=user %}
  {% endfor %}
</div>

---

{% if site.repo_trophies.enabled %}
{% for user in site.data.repositories.github_users %}
{% if site.data.repositories.github_users.size > 1 %}

  <h4>{{ user }}</h4>
  {% endif %}
  <div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% include repository/repo_trophies.liquid username=user %}
  </div>

---

{% endfor %}
{% endif %}
{% endif %}

{% if site.data.repositories.github_repos %}

## GitHub Repositories

<div class="repositories d-flex flex-wrap flex-md-row flex-column justify-content-between align-items-center">
  {% for repo in site.data.repositories.github_repos %}
    {% include repository/repo.liquid repository=repo %}
  {% endfor %}
</div>
{% endif %}

{% if site.data.repositories.other_services %}

## Web Tools

<style>
  .web-tools > .repo {
    display: flex;
    width: 100%;
  }
  .web-tools > .repo > .card {
    width: 100%;
  }
  .web-tools .card-title,
  .web-tools .card-text {
    min-height: 2lh;
  }
  @media (min-width: 768px) {
    .web-tools > .repo {
      flex: 1 1 0;
      max-width: none;
      width: auto;
    }
  }
</style>

<div class="web-tools repositories d-flex flex-wrap flex-md-row flex-column align-items-stretch">
  {% for service in site.data.repositories.other_services %}
    {% include repository/service_card.liquid service=service %}
  {% endfor %}
</div>

<p class="caption text-muted small">
  TCP Congestion Visualizer is inspired by Guido Appenzeller's
  <a href="https://guido.appenzeller.net/anims/" target="_blank" rel="noopener noreferrer">router buffer sizing animations</a>
  and by Appenzeller, Keslassy &amp; McKeown, '<a href="https://web.stanford.edu/class/cs244/papers/SizingRouterBuffersAppenzeller.pdf" target="_blank" rel="noopener noreferrer">Sizing Router Buffers</a>'.
</p>
{% endif %}
