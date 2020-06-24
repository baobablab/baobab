---
layout: page
title:
permalink: /opportunities/
expiration: 200
---

<!-- Section -->
Intership, PhD, PostDoc or engineer positions are offered in the project. Do not hesitate to <a href="mailto:{{site.email}}">contact us.</a>

{% assign today = site.time | date: '%s' %}
{% assign jobs_sorted = site.opportunities | sort: 'date' | reverse %}
{% assign jobs_array = "phd|postdoc|internship" | split: "|" %}

{% for item in jobs_array %}

<div class="major">
{% if item == 'phd' %}
    <h3>PhD Scholarship</h3>
{% elsif item == 'postdoc' %}
    <h3>PostDoctoral position</h3>
{% elsif item == 'internship' %}
    <h3>Internship</h3>
{% elsif item == 'old' %}
    <h3>Already filled position</h3>
{% endif %}
</div>

<div class="posts">
  {% for job in jobs_sorted %}
    {% if job.subcat contains item %}
      {% assign start = job.date | date: '%s' %}
      {% assign seconds_since = today | minus: start %}
      {% assign hours_since = seconds_since | divided_by: 60 | divided_by: 60 %}
      {% assign days_since = hours_since | divided_by: 24 %}
      {% if days_since < site.expiration_opportunities %}
        <article>
          <ul>
            <li>{{job.title}}</li>
            <li>{{job.profile}}</li>
            <center>
            {% if job.ext_url %}
              <a href="{{job.ext_url}}" class="icon fa-cloud-download" target="_blank"><span class="label">Job</span></a>
            {% elsif job.pdf %}
              <a href="{{site.url}}/{{site.baseurl}}/images/opportunities/{{job.pdf}}" class="icon fa-cloud-download" target="_blank"><span class="label">Job</span></a>
            {% else %}
              <a href="mailto:{{site.email}}" class="icon fa-envelope-square" target="_blank"><span class="label">Job</span></a>
            {% endif %}
            </center>
          </ul>
        </article>
      {% endif %}
    {% endif %}
  {% endfor %}
</div>
<hr>

{% endfor %}

