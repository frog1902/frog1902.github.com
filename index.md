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
  
<section>
   <h3>Recent Posts</h3>
   <ul class="post">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
   </ul>
</section>

<section>
   <h3>Latest Comments</h3>
   <ul class="ds-recent-comments" data-num-items="10" data-show-avatars="1" data-show-time="1" data-show-title="1" data-show-admin="1" data-excerpt-length="18"></ul>
</section>

<section style="width:250px;">
    <h3>Recent Visitors</h3>
    <ul class="ds-recent-visitors" data-num-items="4" data-avatar-size="45" style="margin-top:10px;"></ul>
</section>
