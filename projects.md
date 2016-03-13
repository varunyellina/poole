---
layout: page
title: Projects
resource: true
---

<div class="posts-listing">
  {% assign projects-list = site.projects | sort:'listing-order' %}
  {% for project in projects-list reversed %}
    <a href="{{ site.baseurl }}{{ project.url }}" title="">
      <article class="post">
        <h1 class="post-title">
            <img src="{{ project.poster-image }}">
            {{ project.title }}
        </h1>
        {{ project.excerpt }}
      </article>
    </a>
  {% endfor %}
</div>
