---
layout: default
title: Archive
---

<div id="home">
    <ul class="posts">
        {% for post in site.categories.archive %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
        {% endfor %}
    </ul>
</div>
