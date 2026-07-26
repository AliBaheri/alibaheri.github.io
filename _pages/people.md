---
layout: page
permalink: /people/
title: people
description: I have the good fortune to work with a talented group of students in the Safe AI Lab at RIT.
nav: true
nav_order: 6
---

<!-- Plain HTML on purpose: no Jekyll plugins required, so this builds on
     GitHub Pages with no extra setup.
     To add a person, copy a card block and edit the initials, name, role,
     and (optionally) the paper link. Move cards between the "current" and
     "alumni" grids as roles change. -->

<style>
.ppl-grid {
  display: grid; grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
  gap: .9rem; margin: 1.2rem 0 2.6rem;
}
.pcard2 {
  display: flex; gap: .85rem; align-items: flex-start;
  padding: 1rem .95rem; border-radius: 11px;
  border: 1px solid color-mix(in srgb, var(--global-text-color) 13%, transparent);
  background: color-mix(in srgb, var(--global-theme-color) 3%, transparent);
  transition: transform .18s ease, box-shadow .18s ease, border-color .18s ease;
}
.pcard2:hover {
  transform: translateY(-2px); border-color: var(--global-theme-color);
  box-shadow: 0 7px 18px color-mix(in srgb, var(--global-theme-color) 18%, transparent);
}
.pcard2 .av {
  flex: 0 0 auto; width: 2.9rem; height: 2.9rem; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: .92rem; font-weight: 700; color: #fff; letter-spacing: .02em;
  background: var(--global-theme-color);
  background: linear-gradient(135deg, var(--global-theme-color),
    color-mix(in srgb, var(--global-theme-color) 55%, #000));
  box-shadow: 0 2px 7px color-mix(in srgb, var(--global-theme-color) 32%, transparent);
}
.pcard2 .nm { font-weight: 600; font-size: .98rem; line-height: 1.25; }
.pcard2 .rl {
  font-size: .78rem; color: var(--global-theme-color);
  font-weight: 600; margin-top: .12rem;
}
.pcard2 .yr { font-size: .78rem; color: var(--global-text-color-light); margin-top: .05rem; }
.pcard2 .co { font-size: .74rem; color: var(--global-text-color-light); margin-top: .3rem; font-style: italic; }
.ppl-note { font-size: .9rem; color: var(--global-text-color-light); }
</style>

## Current

<div class="ppl-grid">

<div class="pcard2">
<div class="av">CS</div>
<div>
<div class="nm">Chirayu Salgarkar</div>
<div class="rl">Ph.D. Student</div>
<div class="yr">2024 &ndash; present</div>
</div>
</div>

<div class="pcard2">
<div class="av">TA</div>
<div>
<div class="nm">Tyler Alvarez</div>
<div class="rl">Undergraduate Researcher</div>
<div class="yr">2025 &ndash; 2026</div>
</div>
</div>

</div>

## Alumni

<div class="ppl-grid">

<div class="pcard2">
<div class="av">LY</div>
<div>
<div class="nm">Lunet Yifru</div>
<div class="rl">M.S. Student</div>
<div class="yr">2021 &ndash; 2024</div>
</div>
</div>

<div class="pcard2">
<div class="av">JY</div>
<div>
<div class="nm">Joshua Yancosek</div>
<div class="rl">M.S. Student</div>
<div class="yr">2021 &ndash; 2024</div>
</div>
</div>

<div class="pcard2">
<div class="av">SK</div>
<div>
<div class="nm">Shriram Karpoora Sundara Pandian</div>
<div class="rl">M.S. Student</div>
<div class="yr">2025</div>
</div>
</div>

<div class="pcard2">
<div class="av">AP</div>
<div>
<div class="nm">Aniket Narendra Patil</div>
<div class="rl">M.S. Student</div>
<div class="yr">2023 &ndash; 2024</div>
<div class="co">Co-advised with Prof. Cecilia Alm</div>
</div>
</div>

<div class="pcard2">
<div class="av">KG</div>
<div>
<div class="nm">Kaustubh Gaikwad</div>
<div class="rl">M.S. Student</div>
<div class="yr">2023 &ndash; 2024</div>
<div class="co">Co-advised with Prof. Cecilia Alm</div>
</div>
</div>

</div>

<p class="ppl-note" markdown="1">
Interested in safe autonomy, reinforcement learning, or optimal transport? I am always
glad to hear from motivated students &mdash; see my [research](/research/) and get in touch.
</p>
