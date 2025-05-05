---
layout: default
title: Recipes
permalink: /recipes/
---

<div class="page-heading">
  <h1>Family Recipes</h1>
  <p>Some of our favorite dishes.</p>
</div>

<div class="recipe-list-container two-column-layout">
  {% comment %} Sort recipes alphabetically by title {% endcomment %}
  {% assign sorted_recipes = site.recipes | sort: 'title' %}

  {% if sorted_recipes.size > 0 %}
    {% for recipe in sorted_recipes %}
      <article class="recipe-preview-item event-item"> {# Reuse card style #}
        {% if recipe.image %}
        <a href="{{ recipe.url | relative_url }}" class="recipe-preview-image-link">
          <img src="{{ recipe.image | relative_url }}" alt="{{ recipe.title | escape }}" class="recipe-preview-image" loading="lazy">
        </a>
        {% endif %}
        <div class="recipe-preview-content">
            <header>
              <h2 class="recipe-preview-title">
                <a href="{{ recipe.url | relative_url }}">{{ recipe.title | escape }}</a>
              </h2>
            </header>
            {% if recipe.description %}
              <p class="recipe-preview-description">{{ recipe.description | escape }}</p>
            {% endif %}
             <footer class="post-read-more">
               <a href="{{ recipe.url | relative_url }}" class="read-more-btn">View Recipe...</a>
            </footer>
        </div>
      </article>
    {% endfor %}
  {% else %}
    <p style="text-align: center; width: 100%;">No recipes found yet! Add some `.md` files to the `_recipes` directory.</p>
  {% endif %}
</div>
