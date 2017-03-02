---
layout: cv_layout
title: Zivotopis
selected: zivotopis
---

{% for song in site.data.song_list %}
<h3>{{ song.name }}</h3>
<object width="420" height="315" data="{{ song.url }}"></object>
{% endfor %}

TU BUDE MOJ ZIVOTOPIS

{% for song in site.data.song_list %}
<h3>{{ song.name }}</h3>
<iframe width="500" height="315" src="http://www.youtube.com/embed/{{ song.url }}" frameborder="0" allowfullscreen></iframe>
{% endfor %}
