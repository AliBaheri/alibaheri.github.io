---
layout: page
permalink: /blog/
title: blog
description: Occasional notes on the ideas behind our research.
nav: true
nav_order: 5
---

<!-- Plain Liquid on purpose: no pagination plugin required, so this builds
     on GitHub Pages with no extra setup. New posts appear automatically -
     just add a file to _posts/ named YYYY-MM-DD-title.md -->

<style>
.blog-list { list-style: none; padding: 0; margin-top: 1.5rem; }
.blog-list li {
  padding: 1rem 0 1.1rem;
  border-bottom: 1px solid color-mix(in srgb, var(--global-text-color) 12%, transparent);
}
.blog-list li:first-child { border-top: 1px solid color-mix(in srgb, var(--global-text-color) 12%, transparent); }
.blog-list .bt { font-size: 1.12rem; font-weight: 600; line-height: 1.3; }
.blog-list .bt a { text-decoration: none; }
.blog-list .bd { font-size: .74rem; color: var(--global-text-color-light); margin-top: .18rem; }
.blog-list .bx { font-size: .92rem; line-height: 1.55; margin-top: .45rem; }
.blog-list .btag {
  display: inline-block; font-size: .66rem; font-weight: 600; letter-spacing: .04em;
  padding: .08rem .55rem; border-radius: 999px; margin-right: .3rem; margin-top: .5rem;
  color: var(--global-theme-color);
  background: color-mix(in srgb, var(--global-theme-color) 12%, transparent);
}
</style>

<ul class="blog-list">
{% for post in site.posts %}
  <li>
    <div class="bt"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
    <div class="bd">{{ post.date | date: "%B %-d, %Y" }}</div>
    {% if post.description %}<div class="bx">{{ post.description }}</div>{% endif %}
    {% if post.tags %}{% for tag in post.tags %}<span class="btag">{{ tag }}</span>{% endfor %}{% endif %}
  </li>
{% endfor %}
</ul>
