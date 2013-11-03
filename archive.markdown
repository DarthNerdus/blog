---
layout: default
title: Archive
---
<div class="contentpost"><div class="contentpost__linkline">The list of all {{ site.posts.size }} posts.</div></div>
<div style="margin: 20px auto;">
<div markdown="1">
{% for post in site.posts %}{{ post.date | date: "%b %d, %Y" }} |&nbsp;<img class="archive" src="/images/{{ post.layout }}.gif">&nbsp;| <a href="{{ post.url }}">{{ post.title }}</a>
{% endfor %}
</div></div>