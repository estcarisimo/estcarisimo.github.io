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

## Packages

<style>
  .package-chips {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
    margin: 0.25rem 0 1rem;
  }
  .package-chip {
    display: inline-flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.15rem 0.65rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 999px;
    background: var(--global-card-bg-color);
    color: var(--global-text-color);
    font-size: 0.85rem;
    line-height: 1.5;
    text-decoration: none;
    white-space: nowrap;
  }
  .package-chip:hover,
  .package-chip:focus {
    color: var(--global-theme-color);
    border-color: var(--global-theme-color);
    text-decoration: none;
  }
  .package-chip .fab {
    font-size: 0.9em;
  }
  .package-chip-reg {
    color: var(--global-text-color-light);
    font-size: 0.75rem;
  }
  .package-chip:hover .package-chip-reg,
  .package-chip:focus .package-chip-reg {
    color: var(--global-theme-color);
  }
</style>

<div class="package-chips">
  <a class="package-chip" href="https://pypi.org/project/borges/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-python" aria-hidden="true"></i><span>borges</span><span class="package-chip-reg">PyPI</span>
  </a>
  <a class="package-chip" href="https://pypi.org/project/jitterbug-inference/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-python" aria-hidden="true"></i><span>jitterbug-inference</span><span class="package-chip-reg">PyPI</span>
  </a>
  <a class="package-chip" href="https://pypi.org/project/lanet-vi/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-python" aria-hidden="true"></i><span>lanet-vi</span><span class="package-chip-reg">PyPI</span>
  </a>
  <a class="package-chip" href="https://pypi.org/project/levy-stable/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-python" aria-hidden="true"></i><span>levy-stable</span><span class="package-chip-reg">PyPI</span>
  </a>
  <a class="package-chip" href="https://pypi.org/project/bayesian-changepoint/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-python" aria-hidden="true"></i><span>bayesian-changepoint</span><span class="package-chip-reg">PyPI</span>
  </a>
  <a class="package-chip" href="https://pypi.org/project/originet/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-python" aria-hidden="true"></i><span>originet</span><span class="package-chip-reg">PyPI</span>
  </a>
  <a class="package-chip" href="https://crates.io/crates/originet" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-rust" aria-hidden="true"></i><span>originet</span><span class="package-chip-reg">crates.io</span>
  </a>
  <a class="package-chip" href="https://estcarisimo.github.io/smoking-pi/packaging/" target="_blank" rel="noopener noreferrer">
    <i class="fab fa-linux" aria-hidden="true"></i><span>smoking-pi</span><span class="package-chip-reg">apt / brew</span>
  </a>
</div>

{% if site.data.repositories.other_services %}

## Web Tools

<style>
  .web-tools.repositories {
    display: grid;
    grid-template-columns: 1fr;
    align-items: stretch;
  }
  .web-tools > .repo {
    display: flex;
    width: 100%;
    max-width: none;
  }
  .web-tools > .repo > .card {
    width: 100%;
  }
  .web-tools .card-title {
    min-height: 2lh;
  }
  .web-tools .card-text {
    min-height: 4.5lh;
  }
  @media (min-width: 768px) {
    .web-tools.repositories {
      grid-template-columns: 1fr 1fr;
    }
    .web-tools .card-text {
      min-height: 3lh;
    }
  }
</style>

<div class="web-tools repositories">
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

{% include repository/software_jsonld.html %}
