---
layout: default
---

{% assign research_sorted = (site.research | sort: 'added' | reverse  %}

<!-- Section -->
1 {{ site.baseurl }} <br/>
2 {{ site.url }} <br/>
3 {{ application.url }} <br/>
<section>
    <header class="major">
      <h2>Gallery</h2>
    </header>
    <div class="posts">
    {% for research in research_sorted limit: 6 %}
      <article>
        <a href="{{ site.baseurl }}{{ research.url }}" class="image"><img src="{{site.baseurl}}/images/research/{{research.icon}}" alt="" /></a>
        <h3>{{ research.title }}</h3>
        <p>{{ research.teasing }}...</p>
        <ul class="actions">
            <li><a href="{{ site.baseurl }}{{ research.url }}" class="button medium">More</a></li>
        </ul>
      </article>
    {% endfor %}
    </div>
</section>

