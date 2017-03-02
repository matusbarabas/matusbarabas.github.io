---
layout: cv_layout
title: Zivotopis
selected: zivotopis
---

TU BUDE MOJ ZIVOTOPIS

{% for song in site.data.song_list %}
<h3>{{ song.name }}</h3>
<iframe width="500" height="315" src="http://www.youtube.com/embed/{{ song.url }}" frameborder="0" allowfullscreen></iframe>
{% endfor %}
