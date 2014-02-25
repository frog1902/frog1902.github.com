---
layout: page
title: Hello frog!
tagline: About algorithm About life
---
{% include JB/setup %}

# 博客搬家中，请暂时先访问[http://blog.csdn.net/liguan1](http://blog.csdn.net/liguan1)
## 我准备把旧blog上的文章重新整理一下，代码托管到gist上，所以这个博客暂时没什么内容啦，请先移步我的CSDN博客吧，多谢！

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
