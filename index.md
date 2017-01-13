---
title: My blog
layout: default
---
Hello, World!
  {% for post in site.posts %}
    - [{{ post.title }}]({ % post_url {{ post.url }} % })
  {% endfor %}
