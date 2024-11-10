---
layout: page
title: Home
id: home
permalink: /
---

## Welcome! 🌱

<!--<p style="padding: 3em 1em; background: #f5f7ff; border-radius: 4px;">
  Take a look at <span style="font-weight: bold">[[Your first note]]</span> to get started on your exploration.
</p>-->

This is my personal blog where every story begins, even with background stories which build a whole plot.


<strong>Recently written notes</strong>

<ul>
  {% assign recent_notes = site.notes | sort: "date" | reverse %}
  {% for note in recent_notes limit: 10 %}

    <li>
      {{ note.date | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endfor %}
</ul>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>

<div>
<strong>All the seeds and sprouts in this garden</strong>
{% include notes_graph.html %}
<div>
