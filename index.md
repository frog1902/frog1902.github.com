---
layout: page
title: Hello frog!
tagline: About algorithm About life
---
{% include JB/setup %}

    while (is_alive(dream))
    {
      fllow_my_heart(true);
    }
  
# Recent Posts
<ul class="post">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
