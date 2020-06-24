---
layout: page
title:
permalink: /research/category1/
---

{% assign cat = 'category1' %}

<!-- Section -->

{% assign today = site.time | date: '%s' %}
{% assign research_sorted = site.research | where: "cat", cat | sort: 'subcat' %}
{% assign unique_subcats = '' | split: ',' %}
{% for research in research_sorted %}
  <!-- If not equal to previous then it must be unique as sorted -->
  {% unless research.subcat == previous %}
    {% assign unique_subcats = unique_subcats | push: research.subcat %}
  {% endunless %}
  {% assign previous = research.subcat %}
{% endfor %}
{% assign research_sorted = site.research | where: "cat", cat | sort: 'added' | reverse  %}

<h2>{{cat | capitalize}}</h2>

{% for subcat in unique_subcats %}
<header class="major">
<h3>{{subcat | capitalize}}</h3>
</header>
<div class="posts">
{% for research in research_sorted %}
  {% if research.subcat == subcat %}
    <article>
        <a href="{{site.url}}/{{site.baseurl}}/{{research.url}}" class="image"><img src="{{site.url}}/{{site.baseurl}}//images/research/{{research.icon}}" alt="" /></a>
        <h3>{{research.title}}</h3>
        <p>{{research.teasing}}...</p>
        <ul class="actions">
            <li><a href="{{site.url}}/{{site.baseurl}}/{{research.url}}" class="button medium">More</a></li>
        </ul>
    </article>
  {% endif %}
{% endfor %}
</div>
{% endfor %}

<hr>

