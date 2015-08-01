---
title: Recent notes
layout: default
---

### {{ page.title }}

<p>
<ul style="list-style-type:none;">
    {% for post in site.posts %}
    <li>
    {{ post.original_date }}:  <a href="{{ post.url }}">{{ post.title }}</a><br/>

    </li>
    {% endfor %}
</ul>
</p>
