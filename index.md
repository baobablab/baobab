---
layout: default
---

{% assign labs_sorted = site.labs | where: "subcat", "lab" | sort: "title"  %}
{% assign research_sorted = site.research | sort: 'added' | reverse  %}

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
    {% for lab in labs_sorted %}
      <article>
        <a href="{{site.url}}{{site.baseurl}}/{{lab.url}}" class="image"><img src="{{site.url}}{{site.baseurl}}/images/labs/{{lab.icon}}" alt="" /></a>
        <h3>{{ lab.title }}</h3>
        <p>
            <b>Leader: </b>
            <script>mail2("{{lab.leader | replace: " ", "." | downcase}}",
                          "cea", 3, "", "{{lab.leader}}")</script>
        </p>

        <p>{{ lab.teasing }}...</p>
        <ul class="actions">
            <li><a href="{{site.url}}{{site.baseurl}}/{{lab.url}}" class="button medium">More</a></li>
        </ul>
      </article>
    {% endfor %}
    </div>
</section>


<section>
    <header class="major">
      <h2>Gallery</h2>
    </header>
    <div class="posts">
    {% for research in research_sorted limit: 6 %}
      <article>
        <a class="image"><img src="{{site.url}}{{site.baseurl}}/images/research/{{research.icon}}" alt="" /></a>
        <h3>{{ research.title }}</h3>
        <p>{{ research.teasing }}...</p>
      </article>
    {% endfor %}
    </div>
</section>

