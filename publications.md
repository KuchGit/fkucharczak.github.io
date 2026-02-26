---
layout: page
title: Publications
description: Articles, chapitres d'ouvrages et actes de conférences.
permalink: /publications/
---

{% assign pubs_by_year = site.data.publications | sort: "year" | reverse | group_by: "year" %}

{% for group in pubs_by_year %}
## {{ group.name }}

<ul class="pub-list">
  {% for pub in group.items %}
  <li class="pub-item">
    <span class="pub-year">{{ pub.year }}</span>
    <div class="pub-body">
      <div class="pub-title">{{ pub.title }}</div>
      <div class="pub-authors">{{ pub.authors }}</div>
      <div class="pub-venue">{{ pub.venue }}</div>
      <div class="pub-links">
        {% if pub.pdf %}<a class="pub-link" href="{{ pub.pdf }}">PDF</a>{% endif %}
        {% if pub.doi %}<a class="pub-link" href="{{ pub.doi }}">DOI</a>{% endif %}
        {% if pub.arxiv %}<a class="pub-link" href="{{ pub.arxiv }}">arXiv</a>{% endif %}
        {% if pub.code %}<a class="pub-link" href="{{ pub.code }}">Code</a>{% endif %}
        {% if pub.slides %}<a class="pub-link" href="{{ pub.slides }}">Slides</a>{% endif %}
        {% if pub.poster %}<a class="pub-link" href="{{ pub.poster }}">Poster</a>{% endif %}
      </div>
    </div>
  </li>
  {% endfor %}
</ul>
{% endfor %}
