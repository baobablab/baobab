---
title:
layout: page
permalink: /bibliography/selected
---

<h2> Selected publications of the {{site.title}} group </h2>

{% assign today = site.time | date: '%Y' %}
{% assign biblio_sorted = site.biblio | sort: 'year' | reverse %}
{% assign year = today | minus: 5 %}

<div class="bibliography">
  {% for entry in biblio_sorted %}
    {% if entry.year > year and entry.team %}
    <li>
      <div class="text-justify">
        {% if entry.journal %}
            {{entry.author}}: {{entry.title}}, {{entry.journal}} ({{entry.year}})
        {% elsif entry.booktitle %}
            {{entry.author}}: {{entry.title}}, {{entry.booktitle}} ({{entry.year}})
        {% else %}
            {{entry.author}}: {{entry.title}} ({{entry.year}})
        {% endif %}
        {% if entry.doi %}
          <a href="http://doi.org/{{entry.doi}}" class="icon fa-500px" target="_blank"><span class="label">DOI</span></a>
        {% endif %}
      </div>
    </li>
    {% endif %}
  {% endfor %}
</div>
<hr>


