---
layout: page
title: Projects
resource: true
---

<p class="message">
  Listed below are projects that I've worked on at CREO and while in college. Feel free to ping me <a href="https://twitter.com/vyellina">@vyellina</a> with your feedback. :)
</p>

<!-- Collating all categories of projects into one "categories" object -->
{% assign rawcategories = "" %}
{% for project in site.projects %}
    {% assign tcategories = project.categories | join:'|' | append:'|' %}
    {% assign rawcategories = rawcategories | append:tcategories %}
{% endfor %}
{% assign rawcategories = rawcategories | split:'|' | sort %}

<!-- Removing duplicate and empty categories from "categories" object -->
{% assign categories = "" %}
{% for category in rawcategories %}
    {% if category != "" %}
        {% if categories == "" %}
            {% assign categories = category | split:'|' %}
        {% endif %}
        {% unless categories contains category %}
            {% assign categories = categories | join:'|' | append:'|' | append:cat | split:'|' %}
        {% endunless %}
    {% endif %}
{% endfor %}

<div class="posts">
  {% for category in categories %} <!-- Categories loop -->
    <h3>{{ category }}</h3>

    {% for project in site.projects %} <!-- Projects loop -->
      {% if project.categories contains category %}
        <article class="post">
          <img src="{{ project.poster-image }}">
          <h1 class="post-title">
            <a href="{{ site.baseurl }}{{ project.url }}" title="">{{ project.title }}</a>
          </h1>
          {{ project.excerpt }}
        </article>
      {% endif %}
    {% endfor %}

  {% endfor %}
</div>
