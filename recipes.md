---
layout: default
title: Recipes
permalink: /recipes/
---

<div class="page-heading">
  <h1>Family Recipes</h1>
  <p>Some of our favorite dishes.</p>
  <div class="filter-button-container">
     <a href="{{ "/tags/" | relative_url }}" class="filter-tag-btn">Filter by Tag &raquo;</a>
  </div>
</div>

<div class="recipe-list-container two-column-layout">
  {% comment %} Sort recipes alphabetically by title {% endcomment %}
  {% assign sorted_recipes = site.recipes | sort: 'title' %}

  {% if sorted_recipes.size > 0 %}
    {% for recipe in sorted_recipes %}
      {% comment %} Use the include file to display the card {% endcomment %}
      {% include recipe_preview_card.html recipe=recipe %}
    {% endfor %}
  {% else %}
    <p style="text-align: center; width: 100%;">No recipes found yet! Add some `.md` files to the `_recipes` directory.</p>
  {% endif %}
</div>
