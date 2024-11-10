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

Welcome to my digital garden. Or should I say 'the blog'? I prefer the term 'digital garden' because it stores more personality. In this tiny garden on the web server, you can see all plots behind my projects. Sometimes, I upload short stories and poems, too.

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