---
layout: default
---

{% assign research_sorted = site.research | where: "subcat", "unit" | sort: 'added' | reverse  %}

<!-- Section -->
<section>
    <header class="major">
      <h2>Laboratories</h2>
    </header>
    <noscript>
    <p> Please note that email addresses on this site are protected to avoid abuse by spammers.
        You will need a JavaScript-enabled browser to see the email addresses.
    </p>
    </noscript>
    <div class="posts">
    {% for research in research_sorted %}
      <article>
        <a href="{{site.url}}/{{site.baseurl}}/{{research.url}}" class="image"><img src="{{site.url}}/{{site.baseurl}}/images/research/{{research.icon}}" alt="" /></a>
        <h3>{{ research.title }}</h3>
        <p>
            <b>Leader: </b>
            <script>mail2("{{research.leader | replace: " ", "." | downcase}}",
                          "cea", 3, "", "{{research.leader}}")</script>
        </p>

        <p>{{ research.teasing }}...</p>
        <ul class="actions">
            <li><a href="{{site.url}}/{{site.baseurl}}/{{research.url}}" class="button medium">More</a></li>
        </ul>
      </article>
    {% endfor %}
    </div>
</section>

