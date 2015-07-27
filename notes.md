---
title: Notes
layout: default
---

# {{ page.title }}

<h3>
    <a name="welcome-to-github-pages" class="anchor" href="#welcome-to-github-pages"><span class="octicon octicon-link"></span></a>Recent News</h3>
<p>
<ul>
    {% for post in site.posts %}
    <li>
    <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
    {% endfor %}
</ul>
</p>
