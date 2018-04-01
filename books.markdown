---
layout: default
title: Book Reviews
---
<div class="contentpost"><div class="contentpost__linkline">The list of all {{ site.categories.books.size }} book reviews.</div></div>
<div style="margin: 20px auto;">
<div markdown="1">
{% for post in site.categories.books %}{{ post.date | date: "%b %d, %Y" }} |&nbsp;<img class="archive" src="/images/{{ post.layout }}.gif">&nbsp;| <a href="{{ post.url }}">{{ post.title }}</a>
{% endfor %}
</div></div>
