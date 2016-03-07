---
layout: page
title: Projects
resource: true
---

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
    {% for project in site.projects %} <!-- Projects loop -->
      {% if project.categories contains category %}
        <article class="post">
          <h1 class="post-title">
            <a href="{{ site.baseurl }}{{ project.url }}" title="">
              <img src="{{ project.poster-image }}">
              {{ project.title }}
            </a>
          </h1>
          {{ project.excerpt }}
        </article>
      {% endif %}
    {% endfor %}

  {% endfor %}
</div>
