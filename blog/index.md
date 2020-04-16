---
layout: default
title: "GeoCAT Blog"
---
{% include JB/setup %}

## <img align="center" width="10%" height="10%" src="/images/GeoCAT_Final_Logos-03.svg"> Development Blog

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

