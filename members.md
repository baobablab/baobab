---
layout: page
title:
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'joined' %}
{% assign people_array = "pi|postdoc|gradstudent|engineer|alumni" | split: "|" %}
{% assign labs_sorted = site.labs | sort: 'cat' %}
{% assign unique_labs = '' | split: ',' %}
{% for lab in labs_sorted %}
  <!-- If not equal to previous then it must be unique as sorted -->
  {% unless lab.cat == previous %}
    {% assign unique_labs = unique_labs | push: lab.cat %}
  {% endunless %}
  {% assign previous = lab.cat %}
{% endfor %}

<script>
$(document).ready(function() {
    $(".dropdown-menu").change(function () {
        var lab = this.value;
        {% for lab in unique_labs %}
            if (lab == "Choose") {
                $(".{{lab}}").show();
            } else {
                $(".{{lab}}").hide();
            } 
        {% endfor %}
        $("." + lab).show();
    });
});
</script>

<b> Filter by laboratories:</b>
<select class="dropdown-menu">
    <option>Choose</option>
    <option value="ciel">CIEL</option>
    <option value="gaia">GAIA</option>
    <option value="metric">METRIC</option>
</select>

{% for item in people_array %}

<div class="pos_header">
{% if item == 'postdoc' %}
    <h3>Postdoctoral Fellows</h3>
{% elsif item == 'pi' %}
    <h3>Principal Investigators</h3>
{% elsif item == 'gradstudent' %}
    <h3>Graduate Students</h3>
{% elsif item == 'engineer' %}
    <h3>Research Engineers</h3>
{% elsif item == 'visiting' %}
    <h3>Visiting Scholars</h3>
{% elsif item == 'alumni' %}
    <h3>Alumni</h3>
{% endif %}
</div>

<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains item %}
    <div class="list-item-people {{profile.cat}} {{profile.subcat}}">
      <p class="list-post-title">
        {% if profile.site %}
            <a href="{{ profile.site }}">
        {% elsif profile.page %}
            <a href="{{site.url}}/{{site.baseurl}}/{{ profile.url }}">
        {% else %}
            <a>
        {% endif %}
        {% if profile.avatar %}
            <img width="200" src="{{site.url}}/{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
        {% else %}
            <img width="200" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
        {% endif %}
        {% if profile.site %}
            <a class="name" href="{{ profile.site }}">{{ profile.name }}</a>
        {% elsif profile.page %}
            <a class="name" href="{{site.url}}/{{site.baseurl}}/{{ profile.url }}">{{ profile.name }}</a>
        {% else %}
            <a class="name">{{ profile.name }}</a>
        {% endif %}
      </p>
    </div>
    {% endif %}
  {% endfor %}
</div>
<hr>

{% endfor %}
