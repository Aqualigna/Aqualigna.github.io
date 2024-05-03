---
layout: page
title: 学习 Learning
permalink: /learning/
description: 这些页面展示我学习过的部分课程. These pages show some of the courses I have leanrt.
nav: false
display_categories: [基础数学, 应用数学]
horizontal: false
---

<!-- pages/learning.md -->

<div class="learning">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized learning -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_learning = site.learning | where: "category", category %}
  {% assign sorted_learning = categorized_learning | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_learning %}
      {% include learning_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="grid">
    {% for project in sorted_learning %}
      {% include learning.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display learning without categories -->

{% assign sorted_learning = site.learning | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for project in sorted_learning %}
      {% include learning_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>

{% else %}

  <div class="grid">
    {% for project in sorted_learning %}
      {% include learning.liquid %}
    {% endfor %}
  </div>

{% endif %}
{% endif %}

</div>
