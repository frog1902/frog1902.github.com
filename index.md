---
layout: page
title: Hello frog!
tagline: About algorithm, about life
---
{% include JB/setup %}

    while (IsAlive(dream))
    {
      fllow my heart(true);
    }
    
<ul class="recent posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
