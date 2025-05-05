---
layout: default
title: Blog
permalink: /blog/
---

<div class="page-heading">
  <h1>Family Blog</h1>
  <p>Updates, stories, and moments from our life.</p>
</div>

<div class="post-list-container two-column-layout">
  {% assign posts_exist = false %}
  {% for post in site.posts %}
    {% assign posts_exist = true %}
    <article class="post-preview-item event-item"> {# Reusing event-item style for card look #}
      <header>
          <h2 class="post-preview-title">
            <a href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
          </h2>
          <p class="post-meta">
            <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %d, %Y" }}</time>
            {% if post.author %}
              • <span class="post-author">{{ post.author | escape }}</span>
            {% endif %}
          </p>
      </header>
      <div class="post-excerpt">
        {{ post.excerpt }}
      </div>
      <footer class="post-read-more">
         <a href="{{ post.url | relative_url }}" class="read-more-btn">Read More...</a>
      </footer>
    </article>
  {% endfor %}

  {% unless posts_exist %}
     <p style="text-align: center; width: 100%;">No blog posts found yet! Add some `.md` files to the `_posts` directory.</p>
  {% endunless %}
</div>
