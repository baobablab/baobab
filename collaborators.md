---
layout: page
title:
permalink: /collaborators/
---

The {{site.title}} team has developped numerous collaborations with colleagues
in different institutions & companies.


{% assign collaborators_sorted = (site.collaborators | sort: 'subcat' %}
{% assign collaborators_array = '' | split: ',' %}
{% for collab in collaborators_sorted %}
  <!-- If not equal to previous then it must be unique as sorted -->
  {% unless collab.subcat == previous %}
    {% assign collaborators_array = collaborators_array | push: collab.subcat %}
  {% endunless %}
  {% assign previous = collab.subcat %}
{% endfor %}
{% assign collaborators_sorted = (site.collaborators | sort: 'joined' | reverse %}

{% for item in collaborators_array %}

<div class="pos_header">
{% if item == 'academic' %}
    <h3>Academic Institutions</h3>
{% elsif item == 'hospital' %}
    <h3>Hospitals</h3>
{% elsif item == 'company' %}
    <h3>Companies</h3>
{% endif %}
</div>

<div class="content list people">
  {% for collab in collaborators_sorted %}
    {% if collab.subcat contains item %}
    <div class="list-item-people">
      <p class="list-post-title">
        {% if collab.avatar %}
            <a href="{{collab.ext_url}}"><img width="200" src="{{site.url}}/{{site.baseurl}}/images/collaborators/{{collab.avatar}}"></a>
        {% else %}
            <a href="{{collab.ext_url}}"><img width="200" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
        {% endif %}
        <a class="name" href="{{collab.ext_url}}">{{collab.name}}</a>
      </p>
    </div>
    {% endif %}
  {% endfor %}
</div>
<hr>

{% endfor %}
