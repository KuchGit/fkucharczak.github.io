---
layout: page
title: Projets
description: Projets de recherche, logiciels et collaborations en cours ou achevés.
permalink: /projects/
---

{% assign active = site.data.projects | where: "status", "actif" %}
{% assign finished = site.data.projects | where: "status", "terminé" %}

{% if active.size > 0 %}
## En cours

<ul class="project-list">
  {% for project in active %}
  <li class="project-item">
    <div class="project-title">
      {% if project.url %}<a href="{{ project.url }}" target="_blank" rel="noopener">{{ project.title }}</a>
      {% else %}{{ project.title }}{% endif %}
    </div>
    {% if project.funding %}
    <div style="font-size:0.78rem;color:#888;margin:0.2rem 0;">{{ project.funding }}</div>
    {% endif %}
    <p class="project-desc">{{ project.description }}</p>
    <div class="project-tags">
      {% for tag in project.tags %}
      <span class="project-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    <div class="pub-links" style="margin-top:0.5rem;">
      {% if project.github %}<a class="pub-link" href="{{ project.github }}">GitHub</a>{% endif %}
      {% if project.paper %}<a class="pub-link" href="{{ project.paper }}">Article</a>{% endif %}
      {% if project.demo %}<a class="pub-link" href="{{ project.demo }}">Démo</a>{% endif %}
    </div>
  </li>
  {% endfor %}
</ul>
{% endif %}

{% if finished.size > 0 %}
## Terminés

<ul class="project-list">
  {% for project in finished %}
  <li class="project-item">
    <div class="project-title">
      {% if project.url %}<a href="{{ project.url }}" target="_blank" rel="noopener">{{ project.title }}</a>
      {% else %}{{ project.title }}{% endif %}
    </div>
    <p class="project-desc">{{ project.description }}</p>
    <div class="project-tags">
      {% for tag in project.tags %}
      <span class="project-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    <div class="pub-links" style="margin-top:0.5rem;">
      {% if project.github %}<a class="pub-link" href="{{ project.github }}">GitHub</a>{% endif %}
      {% if project.paper %}<a class="pub-link" href="{{ project.paper }}">Article</a>{% endif %}
    </div>
  </li>
  {% endfor %}
</ul>
{% endif %}
