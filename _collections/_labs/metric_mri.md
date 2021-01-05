---
layout: page
title: HUMAN/PRIMATE MRI PLATFORM
cat: metric
subcat: cell
headline:
teasing: 7T MRI for the imaging of human and non-human primates - NeuroSpin's 7T clinical MRI is the first machine of this type installed in France in 2008. The counter-field of the magnet consists of three hundred tons of steel arranged around the magnet as passive shielding. It is a Siemens Healthineers imaging device operating with the SyngoMR VB17 user interface. 
leader: Alexandre Vignaud
icon: metric_mri.png
added: 2020
permalink: cells/metric-mri.html
---

{% assign research_sorted = site.research | where: "cat", "metric" | where: "subcat", "mri" | sort: "added" | reverse  %}

![image-title-here]({{site.url}}{{site.baseurl}}/images/labs/{{page.icon}}){:class="center"}

<b> Leader: </b>
<script>mail2("{{page.leader | replace: " ", "." | downcase}}", "cea", 3, "", "{{page.leader}}")</script>

7T MRI for the imaging of human and non-human primates: NeuroSpin's 7T clinical MRI is the first machine of this type installed in France in 2008. The counter-field of the magnet consists of three hundred tons of steel arranged around the magnet as passive shielding. It is a Siemens Healthineers imaging device operating with the SyngoMR VB17 user interface.

<section>
    <header class="major">
      <h2>Gallery</h2>
    </header>
    <div class="posts">
    {% for research in research_sorted limit: 6 %}
      <article>
        <a href="{{site.url}}{{site.baseurl}}/{{research.url}}" class="image"><img src="{{site.url}}{{site.baseurl}}/images/research/{{research.icon}}" alt="" /></a>
        <h3>{{ research.title }}</h3>
        <p>{{ research.teasing }}...</p>
      </article>
    {% endfor %}
    </div>
</section>
