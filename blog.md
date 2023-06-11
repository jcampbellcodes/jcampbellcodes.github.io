---
layout: default
title: audio programming blog
permalink: /blog/
---

<div class="header-bar">
  <h1>TECH POSTS!</h1>
  <h2>Aside from writing music, I also build music gear for a living. Here are some posts I've made about it over the years.</h2>
  <center>Guitar pedals, synthesizers, embedded systems, game development...</center>
  <center>I hope this helps some folks!</center>
  <br/>
  <hr>
  <br/>
</div>


<ul class="post-list">
    {% for post in site.posts %}
      <li>
        <h2><a class="post-title" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h2>
        <p class="post-meta">{{ post.date | date: '%B %-d, %Y — %H:%M' }}</p>
        <p>{{ post.description }}</p>
        <br/>
        <hr/>
      </li>
    {% endfor %}
</ul>