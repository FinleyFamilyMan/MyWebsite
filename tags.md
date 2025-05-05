{% raw %}
---
layout: default
title: Recipe Tags
permalink: /tags/ # Sets the URL for this page to /MyWebsite/tags/
---

<div class="page-heading">
  <h1>Recipe Tags</h1>
  <p>Browse recipes by selecting a tag below.</p>
  <p style="margin-top: 15px;"><a href="{{ "/recipes/" | relative_url }}">&laquo; Back to All Recipes</a></p>
</div>

<div class="tag-list-container">
  {% comment %}
    Get all unique tags used in the 'recipes' collection.
    The 'jekyll-archives' plugin populates site.tags with tag names mapped to posts.
    We just need the names (keys) here.
  {% endcomment %}
  {% assign recipe_tags = "" | split: "," %} {# Initialize empty array #}
  {% for recipe in site.recipes %}
    {% for tag in recipe.tags %}
      {% assign recipe_tags = recipe_tags | push: tag | uniq %}
    {% endfor %}
  {% endfor %}
  {% assign sorted_tags = recipe_tags | sort_natural %} {# Sort alphabetically, case-insensitive #}

  {% if sorted_tags.size > 0 %}
    <ul class="tag-list">
      {% for tag in sorted_tags %}
        {% comment %} Generate the link using the permalink structure defined in _config.yml {% endcomment %}
        {% assign tag_url = "/recipes/tags/" | append: (tag | slugify) | relative_url %}
        <li><a href="{{ tag_url }}" class="tag-link">{{ tag | escape }}</a></li>
      {% endfor %}
    </ul>
  {% else %}
    <p>No recipe tags found.</p>
  {% endif %}
</div>
{% endraw %}
