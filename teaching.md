---
layout: page
title: Cours & Enseignement
description: Cours dispensés, supports pédagogiques et ressources associées.
permalink: /teaching/
---

{% assign courses_by_year = site.data.courses | sort: "year" | reverse | group_by: "year" %}

{% for group in courses_by_year %}
## {{ group.name }}–{{ group.name | plus: 1 }}

<ul class="course-list">
  {% for course in group.items %}
  <li class="course-item">
    <div class="course-title">
      {% if course.url %}<a href="{{ course.url }}">{{ course.title }}</a>
      {% else %}{{ course.title }}{% endif %}
    </div>
    <div class="course-meta">
      {{ course.level }}{% if course.institution %} &middot; {{ course.institution }}{% endif %}
      {% if course.hours %} &middot; {{ course.hours }}h{% endif %}
    </div>
    {% if course.description %}
    <p class="course-desc">{{ course.description }}</p>
    {% endif %}
    <div class="pub-links">
      {% if course.slides %}<a class="pub-link" href="{{ course.slides }}">Slides</a>{% endif %}
      {% if course.notes %}<a class="pub-link" href="{{ course.notes }}">Notes de cours</a>{% endif %}
      {% if course.code %}<a class="pub-link" href="{{ course.code }}">Code</a>{% endif %}
      {% if course.video %}<a class="pub-link" href="{{ course.video }}">Vidéo</a>{% endif %}
    </div>
  </li>
  {% endfor %}
</ul>
{% endfor %}
