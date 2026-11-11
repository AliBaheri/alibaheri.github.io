---
layout: post
date: 2026-10-16 00:00:00+0000
inline: true
---

**[award]** Our proposal **“Trust-Aware Coordination for Multi-Agent LLM Systems on AWS: A Deployment-Ready Stability and Robustness Layer for Bedrock Agents”** has been selected for an **Amazon Research Award** (**$118,000**, including $50,000 in AWS credits).
<a class="nvid" href="/research/#amazon-award" data-video="/assets/img/amazon-award-explainer.mp4" data-poster="/assets/img/amazon-award-explainer.jpg" aria-label="Watch the one-minute explainer video"><span class="nvid-play"><i class="fas fa-play" aria-hidden="true"></i></span><span class="nvid-long">Watch the one-minute explainer</span><span class="nvid-short">Watch the explainer</span><span class="nvid-dur">1:05</span></a>

<style>
.ntext a.nvid {
  position: relative; display: inline-flex; align-items: center; gap: .55rem; vertical-align: middle; overflow: hidden;
  margin: .2rem 0 .1rem .15rem; padding: .26rem .9rem .26rem .26rem; border-radius: 999px; border: 1.5px solid transparent;
  font-size: .84rem; font-weight: 600; line-height: 1.2; white-space: nowrap; color: #f4f8f9; text-decoration: none;
  background: linear-gradient(#0b1518, #0b1518) padding-box, linear-gradient(110deg, #eda751, #8dd2d7) border-box;
  box-shadow: 0 5px 14px -9px rgba(0, 0, 0, .65);
  transition: transform .18s ease, box-shadow .18s ease;
}
.ntext a.nvid::before {
  content: ""; position: absolute; top: 0; bottom: 0; left: -45%; width: 32%; pointer-events: none;
  background: linear-gradient(100deg, transparent, rgba(255, 255, 255, .2), transparent);
  transform: skewX(-20deg); animation: nvid-sheen 5s ease-in-out infinite;
}
@keyframes nvid-sheen { 0%, 72% { left: -45%; } 100% { left: 135%; } }
.ntext a.nvid:hover, .ntext a.nvid:focus-visible {
  color: #fff; text-decoration: none; transform: translateY(-1px); outline: none;
  box-shadow: 0 0 0 3px rgba(237, 167, 81, .2), 0 10px 22px -12px rgba(237, 167, 81, .6);
}
.nvid-play {
  flex: 0 0 auto; display: inline-flex; align-items: center; justify-content: center;
  width: 1.75rem; height: 1.75rem; border-radius: 50%; padding-left: .1rem;
  font-size: .62rem; color: #1d1409; background: radial-gradient(circle at 35% 30%, #f7c682, #e0911f);
  transition: transform .18s ease;
}
.ntext a.nvid:hover .nvid-play { transform: scale(1.08); }
.nvid-dur { padding-left: .55rem; border-left: 1px solid rgba(255, 255, 255, .2); font-size: .74rem; font-weight: 500; color: #a9bec2; }
.nvid-short { display: none; }
@media (max-width: 400px) { .nvid-long { display: none; } .nvid-short { display: inline; } }
@media (prefers-reduced-motion: reduce) {
  .ntext a.nvid::before { animation: none; display: none; }
  .ntext a.nvid, .nvid-play { transition: none; }
  .ntext a.nvid:hover, .ntext a.nvid:hover .nvid-play { transform: none; }
}
.nvid-modal {
  position: fixed; top: 0; right: 0; bottom: 0; left: 0; z-index: 2000; display: flex; align-items: center; justify-content: center;
  padding: 3.6rem 4vw 2rem; background: rgba(3, 8, 10, .9);
}
.nvid-frame { position: relative; width: 100%; max-width: 1100px; }
.nvid-frame video {
  display: block; width: 100%; max-height: 78vh; border-radius: 12px; background: #05090c;
  box-shadow: 0 0 0 1px rgba(141, 210, 215, .3), 0 30px 80px -20px rgba(0, 0, 0, .85);
}
.nvid-x {
  position: absolute; top: -2.9rem; right: 0; width: 2.3rem; height: 2.3rem; border-radius: 50%; cursor: pointer;
  border: 1px solid rgba(255, 255, 255, .4); background: rgba(255, 255, 255, .08); color: #fff; font-size: 1.35rem; line-height: 1;
}
.nvid-x:hover, .nvid-x:focus-visible { background: rgba(255, 255, 255, .22); outline: none; }
.nvid-frame a.nvid-more { display: inline-block; margin-top: .8rem; font-size: .86rem; font-weight: 600; color: #8dd2d7; }
</style>

<script>
(function () {
  var links = document.querySelectorAll('a.nvid[data-video]');
  for (var i = 0; i < links.length; i++) {
    if (links[i].getAttribute('data-ready')) continue;
    links[i].setAttribute('data-ready', '1');
    links[i].addEventListener('click', openVideo);
  }
  function openVideo(ev) {
    if (ev.metaKey || ev.ctrlKey || ev.shiftKey || ev.altKey || ev.button) return;
    ev.preventDefault();
    var a = ev.currentTarget, back = document.activeElement;
    var box = document.createElement('div');
    box.className = 'nvid-modal';
    box.setAttribute('role', 'dialog');
    box.setAttribute('aria-modal', 'true');
    box.setAttribute('aria-label', 'Explainer video');
    box.innerHTML = '<div class="nvid-frame"><button type="button" class="nvid-x" aria-label="Close video">&times;</button>' +
      '<video controls playsinline preload="auto"></video>' +
      '<a class="nvid-more" href="' + a.getAttribute('href') + '">More about this project on the research page</a></div>';
    var v = box.querySelector('video');
    v.poster = a.getAttribute('data-poster') || '';
    v.src = a.getAttribute('data-video');
    function onKey(e) { if (e.key === 'Escape') close(); }
    function close() {
      v.pause();
      if (box.parentNode) box.parentNode.removeChild(box);
      document.removeEventListener('keydown', onKey);
      document.documentElement.style.overflow = '';
      if (back && back.focus) back.focus();
    }
    box.addEventListener('click', function (e) { if (e.target === box) close(); });
    box.querySelector('.nvid-x').addEventListener('click', close);
    document.addEventListener('keydown', onKey);
    document.body.appendChild(box);
    document.documentElement.style.overflow = 'hidden';
    box.querySelector('.nvid-x').focus();
    var p = v.play();
    if (p && p.catch) p.catch(function () {});
  }
})();
</script>
