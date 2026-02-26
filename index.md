---
layout: default
---
<div class="home-layout">

  <!-- Colonne gauche : identité -->
  <aside class="sidebar">
    <div class="sidebar-photo-placeholder">Photo<br>(180 × 200 px)</div>

    <div class="sidebar-name">{{ site.author.name }}</div>
    <div class="sidebar-role">{{ site.author.title }}</div>
    <div class="sidebar-institution">{{ site.author.institution }}</div>

    <ul class="sidebar-links">
      {% for link in site.author.links %}
      <li>
        <a href="{{ link.url }}" target="_blank" rel="noopener">
          <span class="link-icon">›</span>
          {{ link.label }}
        </a>
      </li>
      {% endfor %}
      <li>
        <a href="mailto:{{ site.author.email }}">
          <span class="link-icon">@</span>
          {{ site.author.email }}
        </a>
      </li>
    </ul>
  </aside>

  <!-- Colonne droite : contenu -->
  <div class="page-content">

    <h2>À propos</h2>
    <p>{{ site.author.bio }}</p>

    <h2>Publications récentes</h2>
    <ul class="pub-list">
      {% assign recent = site.data.publications | sort: "year" | reverse | slice: 0, 3 %}
      {% for pub in recent %}
      <li class="pub-item">
        <span class="pub-year">{{ pub.year }}</span>
        <div class="pub-body">
          <div class="pub-title">{{ pub.title }}</div>
          <div class="pub-authors">{{ pub.authors }}</div>
          <div class="pub-venue">{{ pub.venue }}</div>
          <div class="pub-links">
            {% if pub.pdf %}<a class="pub-link" href="{{ pub.pdf }}">PDF</a>{% endif %}
            {% if pub.doi %}<a class="pub-link" href="{{ pub.doi }}">DOI</a>{% endif %}
            {% if pub.code %}<a class="pub-link" href="{{ pub.code }}">Code</a>{% endif %}
          </div>
        </div>
      </li>
      {% endfor %}
    </ul>
    <p style="margin-top:0.75rem;font-size:0.83rem;">
      → <a href="{{ '/publications/' | relative_url }}">Toutes les publications</a>
    </p>

    <h2>Projets en cours</h2>
    <ul class="project-list">
      {% assign featured = site.data.projects | where: "featured", true | slice: 0, 2 %}
      {% for project in featured %}
      <li class="project-item">
        <div class="project-title">
          {% if project.url %}<a href="{{ project.url }}">{{ project.title }}</a>
          {% else %}{{ project.title }}{% endif %}
        </div>
        <p class="project-desc">{{ project.description }}</p>
        <div class="project-tags">
          {% for tag in project.tags %}
          <span class="project-tag">{{ tag }}</span>
          {% endfor %}
        </div>
      </li>
      {% endfor %}
    </ul>
    <p style="margin-top:0.75rem;font-size:0.83rem;">
      → <a href="{{ '/projects/' | relative_url }}">Tous les projets</a>
    </p>

  </div>
</div>
