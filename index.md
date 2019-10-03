---
layout: default
---

{% assign research_sorted = (site.research | sort: 'added' | reverse  %}

<!-- Section -->
<section>
    <header class="major">
      <h2>Gallery</h2>
    </header>
    <div class="posts">
    {% for research in research_sorted limit: 6 %}
      <article>
        <a href="{{site.url}}/{{site.baseurl}}/{{research.url}}" class="image"><img src="{{site.url}}/{{site.baseurl}}/images/research/{{research.icon}}" alt="" /></a>
        <h3>{{ research.title }}</h3>
        <p>{{ research.teasing }}...</p>
        <ul class="actions">
            <li><a href="{{site.url}}/{{site.baseurl}}/{{research.url}}" class="button medium">More</a></li>
        </ul>
      </article>
    {% endfor %}
    </div>
</section>

