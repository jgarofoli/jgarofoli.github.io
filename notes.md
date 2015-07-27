---
title: Recent notes
layout: default
---

# {{ page.title }}

<p>
<ul>
    {% for post in site.posts %}
    <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
</ul>
</p>
