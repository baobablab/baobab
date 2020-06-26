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
{% assign labs_sorted = site.labs | sort: "cat" %}
{% assign unique_labs = '' | split: ',' %}
{% for lab in labs_sorted %}
  {% if lab.subcat == "team" %}
      {% unless lab.cat == previous %}
        {% assign key = "~" | append: lab.cat %}
        {% assign unique_labs = unique_labs | push: key %}
      {% endunless %}
      {% assign unique_labs = unique_labs | push: lab.title %}
      {% assign previous = lab.cat %}
  {% endif %}
{% endfor %}

<script>
$(document).ready(function() {
    var content = "<option>Choose</option>"
    {% for lab in unique_labs %}
        {% if lab contains "~" %}
            {% assign key = lab | replace: "~", "" %}
            content += "<option value='{{key|downcase|replace: " ", "-"}}'>{{key|upcase}}</option>"
        {% else %}
            content += "<option value='{{lab|downcase|replace: " ", "-"}}'>&nbsp;&nbsp;&nbsp;&nbsp;{{lab|downcase}}</option>"
        {% endif %}       
    {% endfor %}
    $(".dropdown-menu").html(content)
    $(".dropdown-menu").change(function () {
        var lab = this.value;
        {% for lab in unique_labs %}
            {% assign key = lab | replace: "~", "" %}
            if (lab == "Choose") {
                $(".{{key|downcase|replace: " ", "-"}}").show();
            } else {
                $(".{{key|downcase|replace: " ", "-"}}").hide();
            } 
        {% endfor %}
        $("." + lab).show();
    });
});
</script>

<b> Filter by laboratories:</b>
<select class="dropdown-menu">
</select>

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
    {% if job.type contains item %}
      {% assign start = job.date | date: '%s' %}
      {% assign seconds_since = today | minus: start %}
      {% assign hours_since = seconds_since | divided_by: 60 | divided_by: 60 %}
      {% assign days_since = hours_since | divided_by: 24 %}
      {% if days_since < site.expiration_opportunities %}
        <article class="{{job.cat|replace: ' ', '-'}} {{job.subcat|replace: ' ', '-'}}">
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

