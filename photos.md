---
layout: default
title: Photos
permalink: /photos/
---

<div class="page-heading">
  <h1>Photo Albums</h1>
  <p>A collection of memories.</p>
</div>

<div class="album-list-container two-column-layout">
  {% comment %} Sort albums by date descending (newest first). Jekyll does this by default if sort_by: date is in _config.yml, but explicit sorting is safer. {% endcomment %}
  {% assign sorted_albums = site.albums | sort: 'date' | reverse %}

  {% if sorted_albums.size > 0 %}
    {% for album in sorted_albums %}
      <article class="album-preview-item event-item"> 
        <header>
          <h2 class="album-preview-title">
            <a href="{{ album.url | relative_url }}">{{ album.title | escape }}</a>
          </h2>
           <p class="post-meta"><time datetime="{{ album.date | date_to_xmlschema }}">{{ album.date | date: "%B %d, %Y" }}</time></p>
        </header>

        <div class="album-preview-images">
          <a href="{{ album.url | relative_url }}" class="main-image-link">
            {% if album.main_image %}
              <img src="{{ album.main_image | relative_url }}" alt="Main photo for {{ album.title | escape }}" class="album-main-image" loading="lazy">
            {% else %}
              <div class="event-image-placeholder" style="height: 200px;">Missing Main Image</div>
            {% endif %}
          </a>
          <div class="album-thumbnails">
            {% comment %} Show first 4 images that ARE NOT the main image {% endcomment %}
            {% assign thumb_count = 0 %}
            {% for image in album.images %}
               {% if image.url != album.main_image and thumb_count < 4 %}
                  <a href="{{ album.url | relative_url }}"><img src="{{ image.url | relative_url }}" alt="{{ image.alt | escape }}" loading="lazy"></a>
                  {% assign thumb_count = thumb_count | plus: 1 %}
               {% endif %}
            {% endfor %}
          </div>
        </div>

        {% if album.caption %}
        <p class="album-caption">{{ album.caption | escape }}</p>
        {% endif %}

        <footer class="post-read-more">
           <a href="{{ album.url | relative_url }}" class="read-more-btn">View Album...</a>
        </footer>

      </article>
    {% endfor %}
  {% else %}
      <p style="text-align: center; width: 100%;">No photo albums found yet! Add some `.md` files to the `_albums` directory and corresponding images to `assets/images/albums/`.</p>
  {% endif %}
</div>
