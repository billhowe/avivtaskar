---
layout: default
title: Guestbook
permalink: /guestbook.html
---

# Guestbook

Leave a message to honor Alex's memory.

{% for entry in site.data.guestbook %}
  <div class="guestbook-entry">
    <p><strong>{{ entry.name }}</strong> on {{ entry.date | date: "%B %d, %Y" }}</p>
    {% if entry.image %}
      <img src="{{ entry.image }}" alt="User image" style="max-width: 200px;"><br>
    {% endif %}
    <blockquote>{{ entry.message | markdownify }}</blockquote>
  </div>
{% endfor %}
