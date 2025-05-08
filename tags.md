---
layout: default
title: Recipe Tags
permalink: /tags/
---

<div class="page-heading">
  <h1>Recipe Tags</h1>
  <p>Browse recipes by selecting a tag below.</p>
  <p style="margin-top: 15px;"><a href="{{ "/recipes/" | relative_url }}">&laquo; Back to All Recipes</a></p>
</div>

<div class="tag-list-container">
  {% comment %} --- Collect, Clean, and Sort Tags --- {% endcomment %}
  {% assign temp_tags_list = "" | split: "," %}
  {% for recipe_item in site.recipes %}
    {% for tag_from_recipe in recipe_item.tags %}
      {% assign cleaned_tag_for_list = tag_from_recipe | strip %} 
      {% unless cleaned_tag_for_list == "" %} 
        {% assign temp_tags_list = temp_tags_list | push: cleaned_tag_for_list %}
      {% endunless %}
    {% endfor %}
  {% endfor %}
  {% assign unique_tags_list = temp_tags_list | uniq %}
  {% assign sorted_tags_list = unique_tags_list | sort_natural %} 
  {% comment %} --- End Tag Collection --- {% endcomment %}

  {% if sorted_tags_list.size > 0 %}
    <ul class="tag-list">
      {% for current_tag_name in sorted_tags_list %}
        {% assign tag_page_slug = current_tag_name | slugify %} {# e.g., "family favorite" becomes "family-favorite" #}
        {% comment %} Ensure link matches permalink structure EXACTLY, including trailing slash {% endcomment %}
        {% assign final_tag_url = "/recipes/tags/" | append: tag_page_slug | append: "/" | relative_url %}
        <li><a href="{{ final_tag_url }}" class="tag-link">{{ current_tag_name | escape }}</a></li>
      {% endfor %}
    </ul>
  {% else %}
    <p>No recipe tags found.</p>
  {% endif %}
</div>
