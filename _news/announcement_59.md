---
layout: post
date: 2026-10-15 09:00:00-0400
inline: true
---

New blog post: **“Control Language Models: what a robot foundation model is missing.”** A small feedback loop, learned on top of frozen vision and language models, gives a robot a memory, a sense of what cannot be undone, and a supervisor that knows when to stop and ask.<br>
<a class="nblog" href="/research-notes/2026/11/14/control-language-models.html" aria-label="Read the blog post on Control Language Models"><span class="nblog-ico"><i class="fas fa-book-open" aria-hidden="true"></i></span><span class="nblog-long">Read the blog post</span><span class="nblog-short">Blog post</span><span class="nblog-go"><i class="fas fa-arrow-right" aria-hidden="true"></i></span></a>

<style>
.ntext a.nblog {
  position: relative; display: inline-flex; align-items: center; gap: .55rem; vertical-align: middle;
  margin: .2rem 0 .1rem .15rem; padding: .26rem .8rem .26rem .26rem; border-radius: 999px; border: 1.5px solid transparent;
  font-size: .84rem; font-weight: 600; line-height: 1.2; white-space: nowrap; color: #f4f8f9; text-decoration: none;
  background: linear-gradient(#0b1518, #0b1518) padding-box, linear-gradient(110deg, #8dd2d7, #eda751) border-box;
  box-shadow: 0 5px 14px -9px rgba(0, 0, 0, .65);
  transition: transform .18s ease, box-shadow .18s ease;
}
.ntext a.nblog:hover, .ntext a.nblog:focus-visible {
  color: #fff; text-decoration: none; transform: translateY(-1px); outline: none;
  box-shadow: 0 0 0 3px rgba(141, 210, 215, .22), 0 10px 22px -12px rgba(141, 210, 215, .65);
}
.nblog-ico {
  flex: 0 0 auto; display: inline-flex; align-items: center; justify-content: center;
  width: 1.75rem; height: 1.75rem; border-radius: 50%;
  font-size: .68rem; color: #0b1f22; background: radial-gradient(circle at 35% 30%, #c9f0f2, #5fbfc8);
  transition: transform .18s ease;
}
.ntext a.nblog:hover .nblog-ico { transform: scale(1.08); }
.nblog-long, .nblog-short { color: inherit; }
.nblog-short { display: none; }
.nblog-go { font-size: .68rem; color: #a9bec2; transition: transform .18s ease; }
.ntext a.nblog:hover .nblog-go { color: #fff; transform: translateX(3px); }
@media (max-width: 400px) { .nblog-long { display: none; } .nblog-short { display: inline; } }
@media (prefers-reduced-motion: reduce) {
  .ntext a.nblog, .nblog-ico, .nblog-go { transition: none; }
  .ntext a.nblog:hover, .ntext a.nblog:hover .nblog-ico, .ntext a.nblog:hover .nblog-go { transform: none; }
}
</style>
