---
layout: default
title: Archive
---
<h2 id="intro">The list of all {{ site.posts.size }} posts.</h2>
<div>
{% for post in site.posts %}{{ post.date | date: "%b %d, %Y" }} &nbsp;<img class="archive" src="/images/{{ post.layout }}.gif">&nbsp; <a href="{{ post.url }}">{{ post.title }}</a></br>{% endfor %}
</div>