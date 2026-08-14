---
layout: page
permalink: /blog/
title: blog
description: Occasional notes on the ideas behind our research.
nav: true
nav_order: 7
---

<style>
.blog-list { margin-top: 1.6rem; }
.blog-entry {
padding: 1.05rem 0 1.15rem;
border-bottom: 1px solid color-mix(in srgb, var(--global-text-color) 12%, transparent);
}
.blog-entry:first-child {
border-top: 1px solid color-mix(in srgb, var(--global-text-color) 12%, transparent);
}
.blog-entry .bt { font-size: 1.12rem; font-weight: 600; line-height: 1.3; }
.blog-entry .bt a { text-decoration: none; }
.blog-entry .bd { font-size: .74rem; color: var(--global-text-color-light); margin-top: .18rem; }
.blog-entry .bx { font-size: .92rem; line-height: 1.55; margin-top: .45rem; }
.blog-entry .btag {
display: inline-block; font-size: .66rem; font-weight: 600; letter-spacing: .04em;
padding: .08rem .55rem; border-radius: 999px; margin-right: .3rem; margin-top: .5rem;
color: var(--global-theme-color);
background: color-mix(in srgb, var(--global-theme-color) 12%, transparent);
}
</style>

<div class="blog-list">
{% for post in site.posts %}
<div class="blog-entry">
<div class="bt"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></div>
<div class="bd">{{ post.date | date: "%B %-d, %Y" }}</div>
{% if post.description %}<div class="bx">{{ post.description }}</div>{% endif %}
{% if post.tags %}<div>{% for tag in post.tags %}<span class="btag">{{ tag }}</span>{% endfor %}</div>{% endif %}
</div>
{% endfor %}
</div>

{% if site.posts.size == 0 %}
<p style="color: var(--global-text-color-light);">No posts yet.</p>
{% endif %}
