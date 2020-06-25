---
layout: page
title: METRIC
cat: metric
subcat: lab
headline: Research topic
teasing: Difficulty on insensible reasonable in. From as went he they. Preference themselves me as thoroughly partiality considered on in estimating. Middletons acceptance discovered projecting so is so or. In or attachment inquietude remarkably comparison at an. Is surrounded prosperous stimulated am me discretion expression. But truth being state can she china widow. Occasional preference fat remarkably now projecting uncommonly dissimilar. Sentiments projection particular companions interested do at my delightful. Listening newspaper in advantage frankness to concluded unwilling. 
leader: Alexandre Vignaud
icon: image.png
added: 2020
---

{% assign teams_sorted = site.labs | where: "cat", "metric" | where: "subcat", "team" | sort: "title"  %}
{% assign cells_sorted = site.labs | where: "cat", "metric" | where: "subcat", "cell" | sort: "title"  %}

![image-title-here]({{site.url}}/{{site.baseurl}}/images/labs/{{page.icon}}){:class="center"}

<b> Leader: </b>
<script>mail2("{{page.leader | replace: " ", "." | downcase}}", "cea", 3, "", "{{page.leader}}")</script>

Difficulty on insensible reasonable in. From as went he they. Preference themselves me as thoroughly partiality considered on in estimating. Middletons acceptance discovered projecting so is so or. In or attachment inquietude remarkably comparison at an. Is surrounded prosperous stimulated am me discretion expression. But truth being state can she china widow. Occasional preference fat remarkably now projecting uncommonly dissimilar. Sentiments projection particular companions interested do at my delightful. Listening newspaper in advantage frankness to concluded unwilling.

<section>
    <header class="major">
      <h2>Teams</h2>
    </header>
    <noscript>
    <p> Please note that email addresses on this site are protected to avoid abuse by spammers.
        You will need a JavaScript-enabled browser to see the email addresses.
    </p>
    </noscript>
    <div class="posts">
    {% for team in teams_sorted %}
      <article>
        {% if team.site %}
            <a href="{{team.site}}" class="image"><img src="{{site.url}}/{{site.baseurl}}/images/labs/{{team.icon}}" alt="" /></a>
        {% else %}
            <a href="{{site.url}}/{{site.baseurl}}/{{team.url}}" class="image"><img src="{{site.url}}/{{site.baseurl}}/images/labs/{{team.icon}}" alt="" /></a>
        {% endif %}
        <h3>{{ team.title }}</h3>
        <p>
            <b>Leader: </b>
            <script>mail2("{{team.leader | replace: " ", "." | downcase}}",
                          "cea", 3, "", "{{team.leader}}")</script>
        </p>

        <p>{{ team.teasing }}...</p>
        <ul class="actions">
            {% if team.site %}
                <li><a href="{{team.site}}" class="button medium">More</a></li>
            {% else %}
                <li><a href="{{site.url}}/{{site.baseurl}}/{{team.url}}" class="button medium">More</a></li>
            {% endif %}
        </ul>
      </article>
    {% endfor %}
    </div>
</section>


<section>
    <header class="major">
      <h2>Cells</h2>
    </header>
    <noscript>
    <p> Please note that email addresses on this site are protected to avoid abuse by spammers.
        You will need a JavaScript-enabled browser to see the email addresses.
    </p>
    </noscript>
    <div class="posts">
    {% for cell in cells_sorted %}
      <article>
        <a href="{{site.url}}/{{site.baseurl}}/{{cell.url}}" class="image"><img src="{{site.url}}/{{site.baseurl}}/images/labs/{{cell.icon}}" alt="" /></a>
        <h3>{{ cell.title }}</h3>
        <p>
            <b>Leader: </b>
            <script>mail2("{{cell.leader | replace: " ", "." | downcase}}",
                          "cea", 3, "", "{{cell.leader}}")</script>
        </p>

        <p>{{ cell.teasing }}...</p>
        <ul class="actions">
            <li><a href="{{site.url}}/{{site.baseurl}}/{{cell.url}}" class="button medium">More</a></li>
        </ul>
      </article>
    {% endfor %}
    </div>
</section>
