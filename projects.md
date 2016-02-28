---
layout: page
title: Projects
resource: true
---

<p class="message">
  Below is log of my design work. Feel free to send me your critique :)
</p>

<div class="posts">
  {% assign projects = site.projects | sort: 'listing-priority' %}
  {% for project in projects %}
  <article class="post">
    <img src="{{ project.poster-image }}">
    <h1>
      <a href="{{ site.baseurl }}{{ project.url }}" title="">{{ project.title }}</a>
    </h1>
    {{ project.excerpt }}
  </article>
  {% endfor %}
</div>