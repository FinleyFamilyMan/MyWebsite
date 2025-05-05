---
layout: default
title: Home
# index.md automatically becomes the site's root page "/"
---

<div class="welcome-section">
    <h2>Welcome!</h2>
    <div class="event-image-placeholder" style="height: 180px; margin-bottom: 20px;">[Future Welcome Image Area]</div>
    <p>Welcome to our little corner of the internet! We're glad you stopped by. Check out some of our memories on the <a href="{{ '/photos/' | relative_url }}">Photos Page</a>.</p>
</div>

<hr style="margin: 30px 0;">

<div class="latest-post-section">
    <h2>Latest Blog Post</h2>
    {% assign latest_post = site.posts | first %}
    {% if latest_post %}
      <article class="post-preview-item event-item" style="flex: 1 1 100%; background-color: #fff; border: none; padding: 0;"> {# Use full width & remove card bg/border for home page preview #}
          <header>
              <h3 class="post-preview-title" style="font-size: 1.6em;"> {# Make title slightly larger here #}
                <a href="{{ latest_post.url | relative_url }}">{{ latest_post.title | escape }}</a>
              </h3>
              <p class="post-meta">
                <time datetime="{{ latest_post.date | date_to_xmlschema }}">{{ latest_post.date | date: "%B %d, %Y" }}</time>
                {% if latest_post.author %}
                  • <span class="post-author">{{ latest_post.author | escape }}</span>
                {% endif %}
              </p>
          </header>
          <div class="post-excerpt">
            {{ latest_post.excerpt }}
          </div>
          <footer class="post-read-more">
             <a href="{{ latest_post.url | relative_url }}" class="read-more-btn">Read More...</a>
          </footer>
        </article>
    {% else %}
      <p><em>No blog posts yet! Check back soon.</em></p>
    {% endif %}
</div>
<hr style="margin: 30px 0;">

<div class="about-section">
    <h2>About Our Family</h2>
    <div class="about-image-placeholder">[Future Family Photo Area]</div>
    <p>We are the Finley Family! Amelia and Isaac started dating as highschool sweethearts in 2019, where through college their love blossomed and adopted a beautiful Black and Silver Lab named Daisy Blu Finley, or Blu for short.</p>
    <div style="clear:both;"></div> <h3 style="margin-top: 25px; margin-bottom: 15px; color: #006400;">Our Journey So Far...</h3>
    <div class="two-column-layout">
        <div class="event-item">
            <div class="event-image-placeholder">[Future Proposal Image Area - Image1]</div>
            <p>Isaac Proposed on Amelia's Birthday, April 12th, 2023, at Cypress Grove Park, Orlando Florida and she said YES!</p>
        </div>
        <div class="event-item">
            <div class="event-image-placeholder">[Future Wedding Image Area - Image2]</div>
            <p>They had a beautiful wedding together on January 12th, 2024 at the Winter Park Events Center.</p>
        </div>
         <div class="event-item">
            <div class="event-image-placeholder">[Future Life Image Area - Image3]</div>
            <p>...and since then have been living together Happily (with Blu) in Orlando Florida.</p>
        </div>
    </div>
</div>
