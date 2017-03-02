---
layout: about_me_layout
title: Playlist
selected: o_mne
about_me_selected: pesnicky
---

{% for song in site.data.song_list %}
<h3>{{ song.name }}</h3>
{% include youtubePlayer.html id=song.url %}
{% endfor %}
