---
layout: default
title: Reading-notes
---

<div id="Reading-notes">
  <h1>Articles</h1>
  <ul class="posts noList">
    {% for post in site.posts %}
      {% if post.url contains "-notes" %}
        <li>
          <span class="date">{{ post.date | date: "%Y-%m-%d" }}</span>
          <a href="{{ post.url }}">{{ post.title }}</a>
        </li>
      {% endif %}
    {% endfor %}
  </ul>
</div>
