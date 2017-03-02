---
layout: cv_layout
title: Zivotopis
selected: zivotopis
---

{% for song in site.data.song_list %}
<h3>{{ song.name }}</h3>
{% include youtubePlayer.html id=song.url %}
{% endfor %}

TU BUDE MOJ ZIVOTOPIS

{% for song in site.data.song_list %}
<h3>{{ song.name }}</h3>
[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/{{ song.url }}/0.jpg)](https://www.youtube.com/watch?v={{ song.url }})
{% endfor %}
