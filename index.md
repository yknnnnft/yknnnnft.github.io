---
title: My blog
layout: default
---
Hello, World!
  {% for post in site.posts %}
    - [{{ post.title }}]({{ site.baseurl }}{ % {{ post.url }} % })
  {% endfor %}
