---
layout: post
title: Why the geometry of LLMs reasoning might matter?
date: 2026-06-15 09:00:00-0400

tags: reasoning llm optimal-transport interpretability
categories: research-notes
_styles: >
  .post-content { font-size: 1.06rem; line-height: 1.78; } .post-content p { margin-bottom: 1.35rem; } .post-content h2 {
  margin-top: 3rem; margin-bottom: 1rem; font-size: 1.32rem; font-weight: 700;
  padding-bottom: .45rem;
  border-bottom: 2px solid color-mix(in srgb, var(--global-theme-color) 30%, transparent);
  } .lede { font-size: 1.2rem; line-height: 1.62; } .keyline {
  margin: 2.4rem 0; padding: 1.5rem 1.6rem; border-radius: 10px; text-align: center;
  background: linear-gradient(135deg,
  color-mix(in srgb, var(--global-theme-color) 12%, transparent),
  color-mix(in srgb, var(--global-theme-color) 4%, transparent));
  font-size: 1.5rem; font-weight: 700; line-height: 1.3;
  color: var(--global-theme-color); letter-spacing: -.01em;
  } .shift { margin: 2rem 0; } .shift .q {
  display: flex; align-items: flex-start; gap: 1rem;
  padding: .95rem 1.15rem; border-radius: 8px; margin-bottom: .6rem;
  background: color-mix(in srgb, var(--global-text-color) 5%, transparent);
  font-size: 1.02rem; line-height: 1.5;
  } .shift .q.to {
  background: color-mix(in srgb, var(--global-theme-color) 11%, transparent);
  box-shadow: inset 3px 0 0 var(--global-theme-color);
  } .shift .lbl {
  flex: 0 0 2.6rem; font-size: .68rem; font-weight: 700; letter-spacing: .1em;
  text-transform: uppercase; color: var(--global-theme-color); padding-top: .28rem;
  } .takeaway {
  margin: 2.8rem 0 1.5rem; padding: 1.3rem 1.5rem; border-radius: 10px;
  border: 1px solid color-mix(in srgb, var(--global-theme-color) 35%, transparent);
  background: color-mix(in srgb, var(--global-theme-color) 4%, transparent);
  font-size: 1.06rem; line-height: 1.65;
  } .takeaway .tl {
  display: block; font-size: .7rem; font-weight: 700; letter-spacing: .12em;
  text-transform: uppercase; color: var(--global-theme-color); margin-bottom: .5rem;
  } .paper-note {
  margin-top: 2.8rem; padding: 1.1rem 1.3rem; border-radius: 8px; font-size: .92rem;
  line-height: 1.6;
  border: 1px dashed color-mix(in srgb, var(--global-text-color) 25%, transparent);
  } @media (max-width: 576px) {
  .keyline { font-size: 1.18rem; padding: 1.2rem 1rem; }
  .lede { font-size: 1.08rem; }
  }
  /* ---------- live demos ---------- */
  /* the site colours every div and span; inside a panel they follow the panel instead */
  .demo :where(div, span, p, em, strong) { color: inherit; }
  .demo {
    --dm-bg: #180d1b;
    --dm-acc: color-mix(in srgb, var(--global-theme-color) 70%, #fff);
    --dm-t1: #f3eef4;
    --dm-t2: color-mix(in srgb, var(--dm-t1) 70%, var(--dm-bg));
    --dm-line: rgba(255, 255, 255, .08);
    position: relative; margin: 1.6rem auto 1.7rem; max-width: 700px;
    border-radius: 16px; overflow: hidden;
    background: var(--dm-bg); color: var(--dm-t1);
    box-shadow: 0 0 0 1px color-mix(in srgb, var(--global-theme-color) 34%, transparent),
      0 18px 40px -18px color-mix(in srgb, var(--global-theme-color) 60%, transparent);
  }
  html[data-theme='dark'] .demo {
    --dm-bg: #0d1a1f;
    --dm-acc: var(--global-theme-color);
    --dm-t1: #e8eef0;
    box-shadow: 0 0 0 1px color-mix(in srgb, var(--global-theme-color) 40%, transparent),
      0 18px 40px -18px rgba(0, 0, 0, .7);
  }
  .demo-head {
    display: flex; align-items: center; justify-content: space-between; gap: .3rem .8rem; flex-wrap: wrap;
    padding: .6rem 1rem; border-bottom: 1px solid var(--dm-line);
    background: rgba(255, 255, 255, .03);
    font-size: .76rem; color: var(--dm-t2);
  }
  .demo-title { display: inline-flex; align-items: center; gap: .6rem; font-weight: 600; font-size: .84rem; color: var(--dm-t1); }
  .demo-live {
    display: inline-flex; align-items: center; gap: .38rem; padding: .12rem .5rem .12rem .42rem; border-radius: 999px;
    font-size: .6rem; font-weight: 700; letter-spacing: .14em; text-transform: uppercase; color: var(--dm-acc);
    background: color-mix(in srgb, var(--dm-acc) 14%, transparent);
  }
  .demo-live i {
    width: 7px; height: 7px; border-radius: 50%; background: var(--dm-acc);
    box-shadow: 0 0 8px var(--dm-acc); animation: demo-pulse 1.8s ease-in-out infinite;
  }
  @keyframes demo-pulse { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: .3; transform: scale(.65); } }
  .demo-hud { font-variant-numeric: tabular-nums; }
  .demo-hud b { color: var(--dm-t1); font-weight: 600; }
  .demo-hud .dm-ring {
    display: inline-block; width: 10px; height: 10px; margin-right: .35rem; vertical-align: -1px;
    border: 1.5px solid var(--dm-t1); border-radius: 50%;
  }
  .demo canvas { display: block; width: 100%; height: 280px; }
  .demo-drag canvas { touch-action: pan-y; cursor: grab; }
  .demo-foot {
    display: flex; align-items: center; justify-content: space-between; gap: .5rem .8rem; flex-wrap: wrap;
    padding: .6rem 1rem .7rem; border-top: 1px solid var(--dm-line);
    background: rgba(255, 255, 255, .03);
    font-size: .8rem; line-height: 1.45; color: var(--dm-t2);
  }
  .demo-btn {
    font: inherit; font-size: .75rem; font-weight: 600; padding: .32rem 1rem; border-radius: 999px; cursor: pointer;
    color: var(--dm-t1); background: color-mix(in srgb, var(--dm-acc) 22%, transparent);
    border: 1px solid color-mix(in srgb, var(--dm-acc) 70%, transparent);
    transition: background .15s ease, box-shadow .15s ease;
  }
  .demo-btn:hover, .demo-btn:focus-visible {
    background: color-mix(in srgb, var(--dm-acc) 38%, transparent);
    box-shadow: 0 0 14px color-mix(in srgb, var(--dm-acc) 55%, transparent); outline: none;
  }
  @media (max-width: 576px) { .demo canvas { height: 250px; } .demo-head, .demo-foot { padding-left: .8rem; padding-right: .8rem; } }
  @media (prefers-reduced-motion: reduce) { .demo-live i { animation: none; } .demo-btn { transition: none; } }
  /* ---------- figures in this post ---------- */
  .post-content .demo { max-width: none; margin: 2.5rem 0 2.2rem; font-size: 1rem; font-weight: 400; line-height: 1.5; }
  .post-content .demo-foot { font-size: .8rem; }
  /* no leftover focus ring after a mouse click; keyboard focus keeps its own highlight */
  .demo button:focus:not(:focus-visible) { outline: none; }
  .post-content .demo.gxc { margin-bottom: .9rem; }
  .post-content p.gx-figcap {
    max-width: 36rem; margin: 0 auto 2.3rem; text-align: left;
    font-size: .84rem; line-height: 1.55; color: var(--global-text-color-light);
  }
  .gx-warn { color: #f0a84a !important; }
  .gx-cap {
    display: flex; justify-content: space-between; align-items: baseline; gap: .6rem;
    font-size: .62rem; font-weight: 700; letter-spacing: .14em; text-transform: uppercase; color: var(--dm-t2);
  }
  /* figure 1: where the reasoning breaks */
  .gxc-body { display: grid; grid-template-columns: minmax(0, 43fr) minmax(0, 57fr); }
  .gxc-text { padding: .85rem .9rem .95rem 1rem; border-right: 1px solid var(--dm-line); }
  .gxc-map { position: relative; min-width: 0; }
  .gxc-map .gx-cap { position: absolute; left: 1rem; top: .85rem; z-index: 1; pointer-events: none; }
  .gxc-q { margin: .5rem 0 .5rem; font-size: .76rem; line-height: 1.45; color: var(--dm-t2); }
  .post-content ol.gxc-steps { list-style: none; margin: 0; padding: 0; }
  .gxc-steps li {
    display: grid; grid-template-columns: 1.3rem minmax(0, 1fr) 4rem; align-items: center; gap: .5rem;
    margin: 0; padding: .15rem .45rem .15rem .35rem; border-radius: 7px; cursor: pointer;
    font-size: .8rem; line-height: 1.35; color: var(--dm-t1);
    transition: opacity .35s ease, background .2s ease;
  }
  .gx-js .gxc-steps li { opacity: .16; }
  .gx-js .gxc-steps li.on { opacity: 1; }
  .gxc-steps li.on:hover { background: rgba(255, 255, 255, .05); }
  .gxc-steps li.cur, .gxc-steps li.cur:hover { background: rgba(255, 255, 255, .1); }
  .gxc-n {
    display: inline-flex; align-items: center; justify-content: center; width: 1.25rem; height: 1.25rem; border-radius: 50%;
    font-size: .64rem; font-weight: 700; color: var(--dm-t2); border: 1px solid color-mix(in srgb, var(--dm-t1) 32%, transparent);
    transition: background .2s ease, color .2s ease, border-color .2s ease;
  }
  .gxc-steps li.cur .gxc-n { color: var(--dm-bg); background: var(--dm-t1); border-color: var(--dm-t1); }
  .gxc-steps li.slip .gxc-n { color: #1d1409; background: #d97706; border-color: #d97706; }
  .gxc-b { position: relative; height: .4rem; border-radius: 999px; background: rgba(255, 255, 255, .09); }
  .gxc-b::after {
    content: ""; position: absolute; left: 60%; top: -.38rem; bottom: -.38rem;
    border-left: 1px dashed color-mix(in srgb, var(--dm-t1) 60%, transparent);
  }
  .gxc-b i {
    position: absolute; left: 0; top: 0; bottom: 0; width: 0; border-radius: 999px; background: var(--dm-acc);
    transition: width .6s cubic-bezier(.2, .8, .2, 1);
  }
  .gxc-steps li.e .gxc-b i { background: #d97706; }
  .gxc-steps li.p .gxc-b i { background: color-mix(in srgb, #d97706 70%, transparent); }
  .gxc-capb { position: relative; width: 4rem; margin-right: .45rem; text-align: left; letter-spacing: .08em; }
  .gxc-th { position: relative; height: .95rem; margin: .1rem .45rem 0 0; }
  .gxc-th span { position: absolute; right: 1.6rem; transform: translateX(50%); font-size: .6rem; letter-spacing: .04em; color: var(--dm-t2); white-space: nowrap; }
  .gxc-verdict {
    margin-top: .3rem; padding: .5rem .7rem; border-radius: 8px; font-size: .76rem; line-height: 1.5; color: var(--dm-t1);
    background: color-mix(in srgb, #d97706 12%, transparent); border: 1px solid color-mix(in srgb, #d97706 50%, transparent);
    transition: opacity .45s ease;
  }
  .gx-js .gxc-verdict { opacity: 0; }
  .gx-js .gxc-verdict.on { opacity: 1; }
  .gxc-verdict b { color: #f0a84a; font-weight: 700; }
  @media (max-width: 700px) {
    .gxc-body { grid-template-columns: minmax(0, 1fr); }
    .gxc-text { border-right: 0; border-bottom: 1px solid var(--dm-line); padding: .8rem .8rem .85rem; }
    .gxc-map .gx-cap { left: .8rem; }
  }
  @media (prefers-reduced-motion: reduce) { .gxc-steps li, .gxc-b i, .gxc-verdict, .gxc-n { transition: none; } }
  /* shared by the two data figures: key, single-result dots, screen-reader text */
  .gx-sr { position: absolute; width: 1px; height: 1px; margin: -1px; padding: 0; overflow: hidden; clip-path: inset(50%); white-space: nowrap; border: 0; }
  .gx-key { display: flex; flex-wrap: wrap; gap: .25rem 1.1rem; font-size: .72rem; line-height: 1.3; color: var(--dm-t2); }
  .gx-key span { display: inline-flex; align-items: center; gap: .4rem; white-space: nowrap; }
  .gx-key i { display: inline-block; flex: 0 0 auto; }
  .gx-key .k-a, .gx-key .k-b { width: 14px; height: 8px; border-radius: 0 3px 3px 0; background: var(--dm-acc); }
  .gx-key .k-b { background: color-mix(in srgb, var(--dm-t1) 40%, transparent); }
  .gx-key .k-d { width: 8px; height: 8px; border-radius: 50%; background: var(--dm-t1); }
  .gx-key .k-c, .gx-key .k-w { width: 8px; height: 8px; border-radius: 50%; background: var(--dm-acc); }
  .gx-key .k-w { background: #d97706; }
  .gx-key .k-f {
    width: 16px; height: 10px; border-radius: 0 2px 2px 0; background: color-mix(in srgb, #d97706 26%, transparent);
    border-left: 1.5px solid var(--dm-t1);
  }
  .gx-dot {
    position: absolute; top: 50%; left: calc((var(--v) - var(--lo)) / var(--span) * 100%); width: 8px; height: 8px; margin: -4px 0 0 -4px;
    border-radius: 50%; background: var(--dm-t1); box-shadow: 0 0 0 2px var(--dm-bg); outline: none;
  }
  .gx-dot::before { content: ""; position: absolute; left: -8px; right: -8px; top: -8px; bottom: -8px; border-radius: 50%; }
  .gx-dot::after {
    content: attr(data-tip); position: absolute; left: 50%; bottom: calc(100% + 9px); transform: translateX(-50%);
    padding: .22rem .5rem; border-radius: 6px; white-space: nowrap; pointer-events: none;
    font-size: .7rem; font-weight: 600; line-height: 1.3; letter-spacing: 0; color: #17121a; background: var(--dm-t1);
    box-shadow: 0 4px 14px rgba(0, 0, 0, .45); opacity: 0; transition: opacity .12s ease;
  }
  .gx-dot.r::after { left: auto; right: -12px; transform: none; }
  .gx-dot:hover, .gx-dot:focus { z-index: 3; box-shadow: 0 0 0 2px var(--dm-bg), 0 0 0 4px color-mix(in srgb, var(--dm-t1) 55%, transparent); }
  .gx-dot:hover::after, .gx-dot:focus::after { opacity: 1; }
  .demo-tag {
    display: inline-flex; align-items: center; padding: .12rem .55rem; border-radius: 999px;
    font-size: .6rem; font-weight: 700; letter-spacing: .14em; text-transform: uppercase; color: var(--dm-acc);
    background: color-mix(in srgb, var(--dm-acc) 14%, transparent);
  }
  /* figure 2: same model, same data */
  .gxr-body { --lo: 40; --span: 60; padding: .85rem 1.1rem .7rem 1rem; }
  .gxr-body .gx-key { margin-bottom: .75rem; }
  .gxr-row, .gxr-axis { display: grid; grid-template-columns: 8.4rem minmax(0, 1fr) 2.2rem; align-items: center; column-gap: .9rem; }
  .gxr-row { padding: .36rem 0; }
  .gxr-name { font-size: .84rem; font-weight: 600; line-height: 1.2; color: var(--dm-t1); }
  .gxr-name small { display: block; margin-top: .12rem; font-size: .68rem; font-weight: 400; color: var(--dm-t2); }
  .gxr-track { position: relative; height: 1.15rem; }
  .gxr-track::before, .gxr-track::after { content: ""; position: absolute; top: -.44rem; bottom: -.44rem; }
  .gxr-track::before { left: calc(10 / 60 * 100%); border-left: 1px solid color-mix(in srgb, var(--dm-t1) 42%, transparent); }
  .gxr-track::after {
    left: calc(35 / 60 * 100%); right: 0;
    border-left: 1px solid rgba(255, 255, 255, .09); border-right: 1px solid rgba(255, 255, 255, .09);
  }
  .gxr-track i {
    position: absolute; left: calc(10 / 60 * 100%); top: 50%; height: 12px; margin-top: -6px; z-index: 1;
    width: calc((var(--v) - 50) / 60 * 100%); border-radius: 0 4px 4px 0;
    background: color-mix(in srgb, var(--dm-t1) 40%, transparent);
  }
  .gxr-row.g .gxr-track i { background: var(--dm-acc); }
  .gxr-track .gx-dot { z-index: 2; }
  .gxr-track .gx-dot:hover, .gxr-track .gx-dot:focus { z-index: 3; }
  .gxr-val { font-size: .9rem; font-weight: 700; font-variant-numeric: tabular-nums; text-align: right; color: var(--dm-t1); }
  .gx-anim .gxr-track i { transform: scaleX(0); transform-origin: left center; transition: transform .9s cubic-bezier(.2, .8, .2, 1); }
  .gx-anim .gxr-track .gx-dot, .gx-anim .gxr-val { opacity: 0; transition: opacity .4s ease .65s; }
  .gx-anim.gx-in .gxr-track i { transform: none; }
  .gx-anim.gx-in .gxr-track .gx-dot, .gx-anim.gx-in .gxr-val { opacity: 1; }
  .gx-anim.gx-in .gxr-row:nth-of-type(3) .gxr-track i { transition-delay: .07s; }
  .gx-anim.gx-in .gxr-row:nth-of-type(4) .gxr-track i { transition-delay: .14s; }
  .gx-anim.gx-in .gxr-row:nth-of-type(5) .gxr-track i { transition-delay: .21s; }
  .gx-anim.gx-in .gxr-row:nth-of-type(6) .gxr-track i { transition-delay: .28s; }
  .gx-anim.gx-in .gxr-row:nth-of-type(7) .gxr-track i { transition-delay: .35s; }
  .gxr-axis { margin-top: .4rem; }
  .gxr-ticks, .gxs-ticks { position: relative; height: 1.9rem; }
  .gxr-ticks span, .gxs-ticks span {
    position: absolute; left: calc((var(--v) - var(--lo)) / var(--span) * 100%); top: 0; transform: translateX(-50%);
    font-size: .68rem; line-height: 1.25; text-align: center; color: var(--dm-t2); font-variant-numeric: tabular-nums;
  }
  .gxr-ticks span:last-child, .gxs-ticks span:last-child { transform: translateX(-100%); text-align: right; }
  .gxr-ticks small, .gxs-ticks small { display: block; font-size: .62rem; white-space: nowrap; }
  /* figure 3: change the model */
  .gxs-seg { display: inline-flex; padding: 2px; border-radius: 999px; background: rgba(255, 255, 255, .06); box-shadow: inset 0 0 0 1px var(--dm-line); }
  .gxs-seg button {
    font: inherit; font-size: .74rem; font-weight: 600; line-height: 1.3; padding: .26rem .85rem; border: 0; border-radius: 999px; cursor: pointer;
    color: var(--dm-t2); background: transparent; transition: background .2s ease, color .2s ease;
  }
  .gxs-seg button:hover { color: var(--dm-t1); }
  .gxs-seg button.on {
    color: var(--dm-t1); background: color-mix(in srgb, var(--dm-acc) 32%, transparent);
    box-shadow: inset 0 0 0 1px color-mix(in srgb, var(--dm-acc) 75%, transparent);
  }
  .gxs-seg button:focus-visible { outline: 2px solid var(--dm-t1); outline-offset: 1px; }
  .gxs-body { display: grid; grid-template-columns: minmax(0, 1fr) minmax(0, 1fr); }
  .gxs-col { min-width: 0; }
  .gxs-col + .gxs-col { box-shadow: -1px 0 0 var(--dm-line); }
  .gxs-cap { display: flex; flex-wrap: wrap; align-items: baseline; gap: .05rem .6rem; padding: .7rem 1rem .6rem; border-bottom: 1px solid var(--dm-line); }
  .gxs-cap b { font-size: .68rem; font-weight: 700; letter-spacing: .14em; text-transform: uppercase; color: var(--dm-t1); }
  .gxs-cap span { font-size: .76rem; line-height: 1.35; color: var(--dm-t2); }
  .demo.gxs canvas { height: 200px; }
  .gxs-m { --lo: 30; --span: 70; padding: .7rem 1rem .45rem; border-top: 1px solid var(--dm-line); }
  .gxs-mh { display: flex; justify-content: space-between; align-items: baseline; font-size: .7rem; color: var(--dm-t2); }
  .gxs-mh b { font-size: 1.55rem; font-weight: 700; line-height: 1; color: var(--dm-t1); }
  .gxs-track { position: relative; height: 1.15rem; margin-top: .4rem; }
  .gxs-track::before, .gxs-track::after { content: ""; position: absolute; top: -.2rem; bottom: -.2rem; }
  .gxs-track::before { left: calc(20 / 70 * 100%); border-left: 1px solid color-mix(in srgb, var(--dm-t1) 42%, transparent); }
  .gxs-track::after {
    left: calc(45 / 70 * 100%); right: 0;
    border-left: 1px solid rgba(255, 255, 255, .09); border-right: 1px solid rgba(255, 255, 255, .09);
  }
  .gxs-pos, .gxs-neg { position: absolute; top: 50%; height: 12px; margin-top: -6px; z-index: 1; }
  .gxs-pos { left: calc(20 / 70 * 100%); border-radius: 0 4px 4px 0; background: var(--dm-acc); }
  .gxs-neg { right: calc(50 / 70 * 100%); border-radius: 4px 0 0 4px; background: #d97706; }
  .gxs-track .gx-dot { z-index: 2; left: 0; }
  .gxs-track .gx-dot::after { bottom: auto; top: calc(100% + 9px); }
  .gxs-track .gx-dot:hover, .gxs-track .gx-dot:focus { z-index: 3; }
  .gxs-ticks { margin-top: .3rem; }
  .gxs-key { justify-content: center; padding: .55rem 1rem; border-top: 1px solid var(--dm-line); }
  @media (max-width: 560px) {
    .gxr-body { padding: .8rem .8rem .6rem; }
    .gxr-row { grid-template-columns: minmax(0, 1fr) auto; row-gap: .28rem; padding: .42rem 0; }
    .gxr-row .gxr-track { grid-column: 1 / -1; grid-row: 2; }
    .gxr-name small { display: inline; margin: 0 0 0 .45rem; }
    .gxr-axis { grid-template-columns: minmax(0, 1fr); }
    .gxr-axis > div:first-child, .gxr-axis > div:last-child { display: none; }
    .gxr-track::before, .gxr-track::after { top: -.2rem; bottom: -.2rem; }
    .gxs-cap { padding: .6rem .7rem .5rem; }
    .gxs-cap span { font-size: .7rem; }
    .demo.gxs canvas { height: 150px; }
    .gxs-m { padding: .6rem .7rem .4rem; }
    .gxs-mh b { font-size: 1.35rem; }
    .gxs-key { padding: .5rem .7rem; }
  }
  @media (prefers-reduced-motion: reduce) { .gx-anim .gxr-track i, .gx-anim .gxr-track .gx-dot, .gx-anim .gxr-val, .gx-dot::after, .gxs-seg button { transition: none; } }
---

<p class="lede" markdown="1">
A model is working through a problem. At step four it carries a quantity across
incorrectly. Nothing dramatic, no confusion, just a small wrong turn. Steps five through
nine build on it, fluently and confidently. The final answer is wrong.
</p>

Now read the transcript. Step four looks like every other step: same measured tone, same
plausible shape. The error is not hiding. It is simply invisible in the medium we happen
to be watching.

## Why reading the text is not enough

A model producing a reasoning chain is satisfying two constraints at once. One is
**fluency**: does this look like a well-formed continuation? The other is **coherence**:
does this actually follow from what came before? Most of the time the two travel
together, which is why reading a chain of reasoning works as well as it does.

But they are different constraints, and they can come apart. A step can be entirely
fluent and not follow at all.

Text is where fluency lives. It is what was optimized, and it is what you are reading. So
when fluency and coherence separate, a detector that reads the text is not merely
unlucky. It is measuring the wrong quantity.

Which raises the obvious question: is there somewhere else to look?

## Reasoning as a path

Inside a language model, every step is represented by a large collection of numbers
called a hidden state. As the model moves from one step to the next, those states move
too. A chain of reasoning traces a path through a very high-dimensional space.

<div class="keyline">Reasoning has a geometry.</div>

That path is what we studied in GeoReason.

The premise is a claim about *motion*, not location. Correct reasoning ranges widely. It
has to, since it covers different territory as it goes. What stays regular is the
step-to-step transition: the kind of move that follows from a given prefix belongs to a
comparatively narrow family. A first error is a move outside that family. It shows up as
a localized departure, an excursion. Later steps can drift back toward familiar ground,
which is why the moment of departure matters more than where the chain ends up.

<div class="demo gxc" id="gx-chain">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Where the reasoning breaks</span><span class="demo-hud" data-hud></span></div>
<div class="gxc-body">
<div class="gxc-text tex2jax_ignore">
<div class="gx-cap"><span>What you read</span><span class="gxc-capb">instability</span></div>
<div class="gxc-q">A bakery sells 37 + 48 loaves at $4 each. A quarter of the revenue covers costs, two owners split the rest, and each saves 10%. What does each take home?</div>
<ol class="gxc-steps">
<li data-s="1"><span class="gxc-n">1</span><span class="gxc-t">Loaves sold: 37 + 48 = 85.</span><span class="gxc-b"><i></i></span></li>
<li data-s="2"><span class="gxc-n">2</span><span class="gxc-t">Each loaf sells for $4.</span><span class="gxc-b"><i></i></span></li>
<li data-s="3"><span class="gxc-n">3</span><span class="gxc-t">So revenue is 85 &times; 4.</span><span class="gxc-b"><i></i></span></li>
<li data-s="4"><span class="gxc-n">4</span><span class="gxc-t">85 &times; 4 = 320.</span><span class="gxc-b"><i></i></span></li>
<li data-s="5"><span class="gxc-n">5</span><span class="gxc-t">Costs: 320 &divide; 4 = 80.</span><span class="gxc-b"><i></i></span></li>
<li data-s="6"><span class="gxc-n">6</span><span class="gxc-t">Profit: 320 &minus; 80 = 240.</span><span class="gxc-b"><i></i></span></li>
<li data-s="7"><span class="gxc-n">7</span><span class="gxc-t">Per owner: 240 &divide; 2 = 120.</span><span class="gxc-b"><i></i></span></li>
<li data-s="8"><span class="gxc-n">8</span><span class="gxc-t">Savings: 10% of 120 = 12.</span><span class="gxc-b"><i></i></span></li>
<li data-s="9"><span class="gxc-n">9</span><span class="gxc-t">Take-home: 120 &minus; 12 = $108.</span><span class="gxc-b"><i></i></span></li>
</ol>
<div class="gxc-th"><span>threshold</span></div>
<div class="gxc-verdict"><b>$108 is wrong.</b> The answer is $114.75. Step 4 dropped a carry: 85 &times; 4 is 340.</div>
</div>
<div class="gxc-map">
<div class="gx-cap"><span>What the model did</span></div>
<canvas role="img" aria-label="Illustration of one reasoning chain read two ways. On the left, nine written steps of an arithmetic problem all read fluently, although step four contains a slip. On the right, the same nine steps drawn as a path through hidden-state space. Steps one to three stay inside a cloud of coherent transitions. Step four jumps far outside it: the first error. Steps five to nine drift back toward the cloud. An instability bar beside each written step stays low for steps one to three, crosses the threshold at step four, and falls again afterwards."></canvas>
</div>
</div>
<div class="demo-foot"><span>Click a step to inspect it. Illustration, not measured data.</span><button type="button" class="demo-btn" data-act="replay">Replay</button></div>
</div>

<p class="gx-figcap">The same reasoning chain, seen two ways. Read as text, every step is equally fluent and the error leaves no trace. Seen as a trajectory, the steps hold inside a band of coherent transitions until one of them breaks away.</p>

The everyday version of this: you do not need to read someone's mind to notice they have
walked off the trail.

## The part that surprised us

It would be tidy to stop there. The more useful result is the one that complicates it.

We built two detectors. A **teacher** uses step labels to construct a contrastive
geometric lens and score how unstable each transition is. It is accurate, but it is not
deployable, because at deployment you do not have labels. So we distilled it into a
**student** that scores raw hidden states in a single pass, with no labels at all.

In-domain, both beat entropy-based, probing-based, and attention-based baselines.

<div class="demo gxr" id="gx-indomain">
<div class="demo-head"><span class="demo-title"><span class="demo-tag">Data</span>Same model, same data: who finds the wrong steps?</span><span class="demo-hud">step-level AUROC</span></div>
<div class="gxr-body" aria-hidden="true">
<div class="gx-key"><span><i class="k-a"></i>our two detectors</span><span><i class="k-b"></i>baselines</span><span><i class="k-d"></i>one benchmark</span></div>
<div class="gxr-row g"><div class="gxr-name">Teacher<small>uses step labels</small></div><div class="gxr-track"><i style="--v:94.88"></i><span class="gx-dot r" tabindex="-1" style="--v:91" data-tip="ProcessBench 91.0"></span><span class="gx-dot r" tabindex="-1" style="--v:98.5" data-tip="PRM800K 98.5"></span><span class="gx-dot r" tabindex="-1" style="--v:94" data-tip="HaluEval 94.0"></span><span class="gx-dot r" tabindex="-1" style="--v:96" data-tip="TruthfulQA 96.0"></span></div><div class="gxr-val">95</div></div>
<div class="gxr-row g"><div class="gxr-name">Student<small>no labels</small></div><div class="gxr-track"><i style="--v:89.92"></i><span class="gx-dot" tabindex="-1" style="--v:75" data-tip="ProcessBench 75.0"></span><span class="gx-dot r" tabindex="-1" style="--v:99.8" data-tip="PRM800K 99.8"></span><span class="gx-dot r" tabindex="-1" style="--v:88.4" data-tip="HaluEval 88.4"></span><span class="gx-dot r" tabindex="-1" style="--v:96.5" data-tip="TruthfulQA 96.5"></span></div><div class="gxr-val">90</div></div>
<div class="gxr-row"><div class="gxr-name">Linear Probe<small>probing-based</small></div><div class="gxr-track"><i style="--v:81.92"></i><span class="gx-dot" tabindex="-1" style="--v:67.8" data-tip="ProcessBench 67.8"></span><span class="gx-dot r" tabindex="-1" style="--v:91.3" data-tip="PRM800K 91.3"></span><span class="gx-dot" tabindex="-1" style="--v:78.6" data-tip="HaluEval 78.6"></span><span class="gx-dot r" tabindex="-1" style="--v:90" data-tip="TruthfulQA 90.0"></span></div><div class="gxr-val">82</div></div>
<div class="gxr-row"><div class="gxr-name">LLM-Check<small>attention-based</small></div><div class="gxr-track"><i style="--v:58.85"></i><span class="gx-dot" tabindex="-1" style="--v:61.9" data-tip="ProcessBench 61.9"></span><span class="gx-dot" tabindex="-1" style="--v:48" data-tip="PRM800K 48.0"></span><span class="gx-dot" tabindex="-1" style="--v:55.7" data-tip="HaluEval 55.7"></span><span class="gx-dot" tabindex="-1" style="--v:69.8" data-tip="TruthfulQA 69.8"></span></div><div class="gxr-val">59</div></div>
<div class="gxr-row"><div class="gxr-name">TL-Entropy<small>entropy-based</small></div><div class="gxr-track"><i style="--v:56.70"></i><span class="gx-dot" tabindex="-1" style="--v:57.1" data-tip="ProcessBench 57.1"></span><span class="gx-dot" tabindex="-1" style="--v:54.5" data-tip="PRM800K 54.5"></span><span class="gx-dot" tabindex="-1" style="--v:50.8" data-tip="HaluEval 50.8"></span><span class="gx-dot" tabindex="-1" style="--v:64.4" data-tip="TruthfulQA 64.4"></span></div><div class="gxr-val">57</div></div>
<div class="gxr-row"><div class="gxr-name">TL-Perplexity<small>entropy-based</small></div><div class="gxr-track"><i style="--v:53.12"></i><span class="gx-dot" tabindex="-1" style="--v:51.2" data-tip="ProcessBench 51.2"></span><span class="gx-dot" tabindex="-1" style="--v:45.8" data-tip="PRM800K 45.8"></span><span class="gx-dot" tabindex="-1" style="--v:48.4" data-tip="HaluEval 48.4"></span><span class="gx-dot" tabindex="-1" style="--v:67.1" data-tip="TruthfulQA 67.1"></span></div><div class="gxr-val">53</div></div>
<div class="gxr-axis"><div></div><div class="gxr-ticks"><span style="--v:50">50<small>coin flip</small></span><span style="--v:75">75</span><span style="--v:100">100<small>perfect</small></span></div><div></div></div>
</div>
<div class="gx-sr">Step-level AUROC on the same model and data, for ProcessBench, PRM800K, HaluEval and TruthfulQA in that order; 50 is a coin flip. Teacher: 91.0, 98.5, 94.0, 96.0. Student: 75.0, 99.8, 88.4, 96.5. Linear Probe: 67.8, 91.3, 78.6, 90.0. LLM-Check: 61.9, 48.0, 55.7, 69.8. TL-Entropy: 57.1, 54.5, 50.8, 64.4. TL-Perplexity: 51.2, 45.8, 48.4, 67.1.</div>
<div class="demo-foot"><span>Bars are the mean of four benchmarks: ProcessBench, PRM800K, HaluEval and TruthfulQA. Hover or tap a dot for its benchmark. Numbers from the paper, Table 1.</span></div>
</div>

Then we changed the model and changed the dataset. The teacher held up. The student collapsed.

<div class="demo gxs" id="gx-shift">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Now change the model</span><span class="gxs-seg" role="group" aria-label="Model the detectors are tested on"><button type="button" data-act="same" aria-pressed="false">Same model</button><button type="button" class="on" data-act="diff" aria-pressed="true">Different model</button></span></div>
<div class="gxs-body">
<div class="gxs-col">
<div class="gxs-cap"><b>Teacher</b><span>rebuilds its lens from the step labels</span></div>
<canvas role="img" aria-label="Schematic. Dots for correct steps and dots for wrong steps form two separate groups, and the teacher draws its boundary between them. When the model changes, both groups move to new coordinates and the boundary moves with them, so it still separates them."></canvas>
<div class="gxs-m" aria-hidden="true"><div class="gxs-mh"><span>step-level AUROC</span><b data-v>91</b></div><div class="gxs-track"><i class="gxs-pos" style="width:58.38%"></i><i class="gxs-neg" style="width:0.00%"></i></div><div class="gxs-ticks"><span style="--v:50">50<small>coin flip</small></span><span style="--v:75">75</span><span style="--v:100">100</span></div></div>
</div>
<div class="gxs-col">
<div class="gxs-cap"><b>Student</b><span>one boundary, learned once, no labels</span></div>
<canvas role="img" aria-label="Schematic. The same two groups of dots. On the model it learned from, the student draws its boundary between them. When the model changes, both groups move to new coordinates but the boundary stays where it was, so it cuts through both groups and no longer separates them."></canvas>
<div class="gxs-m" aria-hidden="true"><div class="gxs-mh"><span>step-level AUROC</span><b data-v>44</b></div><div class="gxs-track"><i class="gxs-pos" style="width:0.00%"></i><i class="gxs-neg" style="width:7.93%"></i></div><div class="gxs-ticks"><span style="--v:50">50<small>coin flip</small></span><span style="--v:75">75</span><span style="--v:100">100</span></div></div>
</div>
</div>
<div class="gx-key gxs-key" aria-hidden="true"><span><i class="k-c"></i>correct steps</span><span><i class="k-w"></i>wrong steps</span><span><i class="k-f"></i>flagged as wrong</span></div>
<div class="gx-sr">Step-level AUROC from the paper, where 50 is a coin flip. Teacher: 91.5 to 91.7 when tested on the model it was trained on, and 90.1 to 91.7 on a different model. Student: 93.5 to 93.9 on the same model, and 33.4 to 58.5 on a different model.</div>
<div class="demo-foot"><span>Top: a schematic of the explanation. The structure is shared, but each model keeps it in its own coordinates. Bottom: measured, from the paper (Tables 3 and 4). Bars are means over train-on, test-on pairs of Qwen, Llama and Mistral; dots are single pairs. The benchmark swap is in Table 5.</span></div>
</div>

That gap is the finding worth carrying out of the paper. The teacher's transfer says the
geometric signal is not an artifact of one model or one benchmark. The structure is
shared. What fails to transfer is the *decision boundary*. The margin separating coherent
transitions from excursions shifts when the distribution shifts, and a student that has
learned where the boundary sat no longer finds it.

So the obstacle to deploying this is not detecting the signal. It is preserving the
margin under shift. That is a narrower problem than "generalization is hard".

## The question this changes

<div class="shift">
<div class="q"><span class="lbl">from</span><span>&ldquo;Does this sentence look wrong?&rdquo;</span></div>
<div class="q to"><span class="lbl">to</span><span>&ldquo;Does this step move the way steps move when reasoning is going well?&rdquo;</span></div>
</div>

These are not the same question, and the second one is answerable from a quantity the
first cannot see.

There is a broader habit underneath this. We tend to evaluate reasoning the way we grade
an exam: check the final answer, maybe skim the working. But reasoning is a process, and
processes have dynamics. If a failure leaves a signature in how a model moves, then what
matters is not only that it arrived somewhere wrong.

The result leaves a harder question open. We found evidence that the first wrong step can
have a geometric signature, but not that every wrong step must have one. Some errors may
move through hidden space almost exactly as correct reasoning does. And even when the
signal exists, our student results show that detecting it reliably across models and
datasets is another problem entirely. What, then, makes the geometry of a reasoning
failure stable? Is there a representation in which the transport margin survives model
and task changes? Or are these signatures inherently local to a particular model's
internal coordinates? Those questions seem more important now than simply asking whether
a model "knows" that it is wrong.

<div class="takeaway" markdown="1">
<span class="tl">The takeaway</span>
Understanding reasoning may require looking not just at where a model ends up, but at the
path it took, and at the point where that path turned.
</div>

<div class="paper-note" markdown="1">
**The paper:** *Where Does Reasoning Break? Step-Level Hallucination Detection via
Hidden-State Transport Geometry*, available on
[arXiv](https://arxiv.org/abs/2605.13772){:target="_blank"}. The geometry we use to
measure those departures comes from optimal transport, a thread that runs through much of
our [research](/research/).
</div>

<script>
(function () {
'use strict';
var DOC = document.documentElement, WHITE = [255, 255, 255];
function css(n) { return getComputedStyle(DOC).getPropertyValue(n).trim(); }
function hex(s) {
if (!s || s.charAt(0) !== '#') return null;
if (s.length === 4) s = '#' + s[1] + s[1] + s[2] + s[2] + s[3] + s[3];
return [parseInt(s.slice(1, 3), 16), parseInt(s.slice(3, 5), 16), parseInt(s.slice(5, 7), 16)];
}
function mixc(a, b, t) { return [0, 1, 2].map(function (i) { return Math.round(a[i] * (1 - t) + b[i] * t); }); }
function col(c, a) { return a == null ? 'rgb(' + c.join(',') + ')' : 'rgba(' + c.join(',') + ',' + a + ')'; }
function sprite(c) {
var s = document.createElement('canvas'), n = 64, g = s.getContext('2d');
s.width = s.height = n;
var gr = g.createRadialGradient(n / 2, n / 2, 0, n / 2, n / 2, n / 2);
gr.addColorStop(0, col(mixc(c, WHITE, 0.55), 1));
gr.addColorStop(0.16, col(c, 0.9));
gr.addColorStop(0.42, col(c, 0.26));
gr.addColorStop(1, col(c, 0));
g.fillStyle = gr; g.fillRect(0, 0, n, n);
return s;
}
/* Panel palette. Validated on the dark panels: accent, amber and gray pass the
   CVD and normal-vision floors pairwise, and all clear 3:1 against the panel. */
var P = {};
function palette() {
var dark = DOC.getAttribute('data-theme') === 'dark';
var theme = hex(css('--global-theme-color')) || (dark ? [38, 152, 186] : [181, 9, 172]);
P.dark = dark;
P.bg = dark ? [13, 26, 31] : [24, 13, 27];
P.t1 = dark ? [232, 238, 240] : [243, 238, 244];
P.t2 = mixc(P.bg, P.t1, 0.7);
P.acc = dark ? theme : mixc(theme, WHITE, 0.3);
P.warn = [217, 119, 6];
P.mut = mixc(P.bg, WHITE, dark ? 0.68 : 0.6);
P.hair = mixc(P.bg, WHITE, 0.17);
P.rod = mixc(P.bg, P.t1, 0.5);
P.sAcc = sprite(P.acc); P.sWarn = sprite(P.warn); P.sMut = sprite(P.mut);
}
palette();
var REDUCE = !!(window.matchMedia && window.matchMedia('(prefers-reduced-motion: reduce)').matches);
var FONT = getComputedStyle(document.body).fontFamily || 'sans-serif';
function rng(seed) {
return function () {
seed = seed + 0x6D2B79F5 | 0;
var t = Math.imul(seed ^ seed >>> 15, 1 | seed);
t = t + Math.imul(t ^ t >>> 7, 61 | t) ^ t;
return ((t ^ t >>> 14) >>> 0) / 4294967296;
};
}
function gauss(r) { var u = 1 - r(), v = r(); return Math.sqrt(-2 * Math.log(u)) * Math.cos(2 * Math.PI * v); }
function ease(t) { return t < 0.5 ? 4 * t * t * t : 1 - Math.pow(-2 * t + 2, 3) / 2; }
function clamp(x, a, b) { return Math.max(a, Math.min(b, x)); }
function circle(c, x, y, r) { c.beginPath(); c.arc(x, y, Math.max(r, 0.1), 0, 2 * Math.PI); }
function rrect(c, x, y, w, h, r) {
r = Math.min(r, w / 2, h / 2);
c.beginPath();
c.moveTo(x + r, y); c.lineTo(x + w - r, y); c.arcTo(x + w, y, x + w, y + r, r);
c.lineTo(x + w, y + h - r); c.arcTo(x + w, y + h, x + w - r, y + h, r);
c.lineTo(x + r, y + h); c.arcTo(x, y + h, x, y + h - r, r);
c.lineTo(x, y + r); c.arcTo(x, y, x + r, y, r); c.closePath();
}
function glow(c, spr, x, y, size, a) {
c.globalAlpha = a == null ? 1 : a;
c.drawImage(spr, x - size / 2, y - size / 2, size, size);
c.globalAlpha = 1;
}
function add(c, on) { c.globalCompositeOperation = on ? 'lighter' : 'source-over'; }
function label(c, s, x, y, o) {
o = o || {};
c.font = (o.w || 400) + ' ' + (o.size || 12) + 'px ' + FONT;
c.textAlign = o.align || 'left'; c.textBaseline = 'alphabetic';
c.shadowColor = col(P.bg, 0.95); c.shadowBlur = 6;
c.globalAlpha = o.a == null ? 1 : o.a;
c.fillStyle = col(o.color || P.t2); c.fillText(s, x, y);
c.shadowBlur = 0; c.globalAlpha = 1;
return c.measureText(s).width;
}
function warnMark(c, x, y, a) {
c.globalAlpha = a == null ? 1 : a;
c.beginPath(); c.moveTo(x, y - 9.5); c.lineTo(x + 6, y + 1); c.lineTo(x - 6, y + 1); c.closePath();
c.fillStyle = col(P.warn); c.fill();
c.fillStyle = col(P.bg); c.fillRect(x - 0.75, y - 6, 1.5, 3.6); c.fillRect(x - 0.75, y - 1.4, 1.5, 1.5);
c.globalAlpha = 1;
}
function makeBg(d) {
var b = d.bgc || (d.bgc = document.createElement('canvas'));
b.width = d.cv.width; b.height = d.cv.height;
var g = b.getContext('2d'), w = b.width, h = b.height, s = d.dpr, x, y;
g.fillStyle = col(P.bg); g.fillRect(0, 0, w, h);
var rg = g.createRadialGradient(w * 0.5, h * 0.42, 0, w * 0.5, h * 0.42, Math.max(w, h) * 0.62);
rg.addColorStop(0, col(P.acc, P.dark ? 0.13 : 0.15)); rg.addColorStop(1, col(P.acc, 0));
g.fillStyle = rg; g.fillRect(0, 0, w, h);
g.fillStyle = col(WHITE, 0.075);
var step = 22 * s, dot = Math.max(1, Math.round(s));
for (y = step / 2; y < h; y += step) for (x = step / 2; x < w; x += step) g.fillRect(Math.round(x), Math.round(y), dot, dot);
}
var demos = [];
function demo(id, setup) {
var el = document.getElementById(id);
if (!el) return;
var cv = el.querySelector('canvas');
if (!cv || !cv.getContext) return;
var d = { el: el, cv: cv, ctx: cv.getContext('2d'), W: 0, H: 0, dpr: 1, run: false, last: 0, hud: el.querySelector('[data-hud]') };
d.size = function () {
d.dpr = Math.min(window.devicePixelRatio || 1, 2);
if (d.heightFor) cv.style.height = d.heightFor(cv.clientWidth) + 'px';
d.W = cv.clientWidth; d.H = cv.clientHeight;
if (!d.W || !d.H) return;
cv.width = Math.round(d.W * d.dpr); cv.height = Math.round(d.H * d.dpr);
d.ctx.setTransform(d.dpr, 0, 0, d.dpr, 0, 0);
makeBg(d);
if (d.layout) d.layout();
};
d.clear = function () {
var c = d.ctx;
c.globalCompositeOperation = 'source-over'; c.globalAlpha = 1; c.setLineDash([]);
c.drawImage(d.bgc, 0, 0, d.W, d.H);
};
d.loop = function (tok) {
return function f(now) {
if (!d.run || tok !== d.tok) return;
var dt = d.last ? Math.min((now - d.last) / 1000, 0.05) : 0;
d.last = now;
if (d.W) { d.step(dt); d.draw(); }
requestAnimationFrame(f);
};
};
d.start = function () { if (!d.run && !REDUCE) { d.run = true; d.last = 0; d.tok = (d.tok || 0) + 1; requestAnimationFrame(d.loop(d.tok)); } };
d.stop = function () { d.run = false; };
d.paint = function (force) { if (!d.W) return; if (REDUCE && d.still && (force || !d.stilled)) { d.stilled = true; d.still(); } else d.draw(); };
d.setHud = function (h) { if (d.hud && d.hudText !== h) { d.hud.innerHTML = h; d.hudText = h; } };
d.pt = function (e) { var b = cv.getBoundingClientRect(); return [e.clientX - b.left, e.clientY - b.top]; };
setup(d);
d.size();
d.paint();
if (!REDUCE) {
if ('IntersectionObserver' in window) {
new IntersectionObserver(function (en) { if (en[en.length - 1].isIntersecting) d.start(); else d.stop(); }, { threshold: 0.1 }).observe(el);
} else {
d.start();
}
}
Array.prototype.forEach.call(el.querySelectorAll('[data-act]'), function (b) {
b.addEventListener('click', function () { d.act(b.getAttribute('data-act'), b); if (!d.run) d.paint(true); });
});
demos.push(d);
}
/* ================================================================
   1. Where the reasoning breaks. An illustrative nine-step chain with a slip at
   step 4. Left: the written steps, each with an instability bar and the
   first-crossing threshold. Right: the same steps as a path in hidden-state
   space. Steps 1-3 stay among coherent transitions, step 4 is the first error
   (a jump outside), and later steps drift back toward the cloud, as the paper
   reports for post-error states. Positions and bar lengths are schematic.
   ================================================================ */
demo('gx-chain', function (d) {
var el = d.el, lis = el.querySelectorAll('.gxc-steps li'), verdict = el.querySelector('.gxc-verdict'), textCol = el.querySelector('.gxc-text');
var N = 9, ERR = 3;
var PTS = [[0.13, 0.70], [0.25, 0.47], [0.40, 0.66], [0.80, 0.17], [0.90, 0.44], [0.79, 0.69], [0.65, 0.86], [0.49, 0.83], [0.32, 0.84]];
var SCORE = [0.2, 0.3, 0.24, 1, 0.72, 0.5, 0.36, 0.27, 0.22];
var BEND = [0, 0.22, -0.2, -0.16, -0.3, -0.2, -0.16, -0.1, 0.1];
var MOVE = 0.6, STEP = 1.05, DWELL = 1.4, HOLD = 5.2, starts = [], total = 0.5, i;
for (i = 0; i < N; i++) { starts.push(total); total += STEP + (i === ERR ? DWELL : 0); }
var clock = 0, pause = 0, fade = 0, phase = 0, pt = 0, time = 0, last = '', pick = -1, hover = -1, geo = null, cloud = null, cloudKey = '';
for (i = 0; i < N; i++) lis[i].classList.add(i < ERR ? 'c' : i === ERR ? 'e' : 'p');
el.classList.add('gx-js');
d.heightFor = function () { return el.offsetWidth < 700 ? 250 : Math.max(300, textCol.offsetHeight); };
d.layout = function () {
var W = d.W, H = d.H;
geo = { W: W, H: H, top: 34, nr: W < 380 ? 9 : 10.5 };
geo.px = function (p) { return [W * (0.04 + p[0] * 0.92), geo.top + (H - geo.top - 8) * p[1]]; };
makeCloud();
};
function rad(th) { return 1 + 0.09 * Math.sin(2 * th + 0.6) + 0.06 * Math.sin(3 * th - 1.1); }
/* the family of coherent transitions: a soft region with many past transitions inside it */
function makeCloud() {
var cv = cloud || (cloud = document.createElement('canvas'));
cv.width = d.cv.width; cv.height = d.cv.height;
var g = cv.getContext('2d'), ce = geo.px([0.36, 0.6]), rx = geo.W * 0.92 * 0.29, ry = (geo.H - geo.top - 8) * 0.34, k, th, q;
g.setTransform(d.dpr, 0, 0, d.dpr, 0, 0);
g.beginPath();
for (k = 0; k <= 72; k++) { th = k / 72 * 2 * Math.PI; q = rad(th); if (k) g.lineTo(ce[0] + Math.cos(th) * rx * q, ce[1] + Math.sin(th) * ry * q); else g.moveTo(ce[0] + rx * q, ce[1]); }
g.closePath();
var gr = g.createRadialGradient(ce[0], ce[1], 0, ce[0], ce[1], Math.max(rx, ry) * 1.1);
gr.addColorStop(0, col(P.acc, 0.3)); gr.addColorStop(1, col(P.acc, 0.07));
g.fillStyle = gr; g.fill();
g.setLineDash([4, 4]); g.strokeStyle = col(P.acc, 0.5); g.lineWidth = 1.1; g.stroke(); g.setLineDash([]);
var rr = rng(5);
g.fillStyle = col(mixc(P.acc, WHITE, 0.3), 0.5);
for (k = 0; k < 150; k++) { th = rr() * 2 * Math.PI; q = Math.sqrt(rr()) * 0.9 * rad(th); circle(g, ce[0] + Math.cos(th) * rx * q, ce[1] + Math.sin(th) * ry * q, 1.15); g.fill(); }
geo.ce = ce; geo.rx = rx; geo.ry = ry;
}
function ctrl(k) {
var a = geo.px(PTS[k - 1]), b = geo.px(PTS[k]), dx = b[0] - a[0], dy = b[1] - a[1];
return [a, [(a[0] + b[0]) / 2 - dy * BEND[k], (a[1] + b[1]) / 2 + dx * BEND[k]], b];
}
function bez(q, u) { var v = 1 - u; return [v * v * q[0][0] + 2 * v * u * q[1][0] + u * u * q[2][0], v * v * q[0][1] + 2 * v * u * q[1][1] + u * u * q[2][1]]; }
function seg(c, q, u) { c.beginPath(); c.moveTo(q[0][0], q[0][1]); for (var k = 1; k <= 26; k++) { var p = bez(q, u * k / 26); c.lineTo(p[0], p[1]); } }
function pop(a) { return a >= 1 ? 1 : 1 + 2.7 * Math.pow(a - 1, 3) + 1.7 * Math.pow(a - 1, 2); }
function sync(force) {
var k = 0, j;
for (j = 0; j < N; j++) if (clock >= starts[j]) k++;
var done = clock >= total, cur = pick >= 0 ? pick : k - 1, key = k + '|' + cur + '|' + done;
if (key === last && !force) return;
last = key;
for (j = 0; j < N; j++) {
lis[j].classList.toggle('on', j < k); lis[j].classList.toggle('cur', j === cur);
lis[j].querySelector('i').style.width = j < k ? (SCORE[j] * 100) + '%' : '0';
}
verdict.classList.toggle('on', done); lis[ERR].classList.toggle('slip', done);
d.setHud(cur < 0 ? 'step <b>&ndash;</b> of 9' : 'step <b>' + (cur + 1) + '</b> of 9 &middot; ' + (cur < ERR ? 'coherent' : cur === ERR ? '<b class="gx-warn">first error</b>' : 'built on the error'));
}
d.step = function (dt) {
time += dt;
if (pause > 0) pause -= dt;
else if (phase === 0) { clock += dt; if (clock >= total + HOLD) { phase = 1; pt = 0; } }
else if (phase === 1) { pt += dt; fade = Math.min(1, pt / 0.45); if (pt >= 0.45) { clock = 0; phase = 2; pt = 0; } }
else { pt += dt; fade = Math.max(0, 1 - pt / 0.45); if (pt >= 0.45) { fade = 0; phase = 0; } }
sync();
};
d.draw = function () {
d.clear();
if (!geo) return;
var c = d.ctx, k, u, q, p, a, key = P.acc.join(',') + d.cv.width;
if (cloudKey !== key) { cloudKey = key; makeCloud(); }
c.drawImage(cloud, 0, 0, d.W, d.H);
label(c, 'coherent transitions', geo.ce[0] - geo.rx * 0.98, geo.ce[1] - geo.ry * 1.13, { size: 11.5, color: P.acc });
/* the moves, in order */
for (k = 1; k < N; k++) {
u = clamp((clock - starts[k]) / MOVE, 0, 1);
if (u <= 0) break;
q = ctrl(k); u = ease(u);
if (k < ERR) { add(c, true); seg(c, q, u); c.strokeStyle = col(P.acc, 0.3); c.lineWidth = 7; c.stroke(); add(c, false); seg(c, q, u); c.strokeStyle = col(P.acc); c.lineWidth = 2.2; c.stroke(); }
else if (k === ERR) { add(c, true); seg(c, q, u); c.strokeStyle = col(P.warn, 0.34); c.lineWidth = 9; c.stroke(); add(c, false); seg(c, q, u); c.strokeStyle = col(P.warn); c.lineWidth = 2.8; c.stroke(); }
else { c.setLineDash([5, 5]); seg(c, q, u); c.strokeStyle = col(P.warn, 0.62); c.lineWidth = 1.8; c.stroke(); c.setLineDash([]); }
if (u < 1) { p = bez(q, u); add(c, true); glow(c, k < ERR ? P.sAcc : P.sWarn, p[0], p[1], 26, 0.95); add(c, false); }
}
/* the steps */
var cur = pick >= 0 ? pick : -1;
if (cur < 0) for (k = 0; k < N; k++) if (clock >= starts[k]) cur = k;
c.textAlign = 'center'; c.textBaseline = 'middle';
for (k = 0; k < N; k++) {
a = clamp((clock - starts[k] - (k ? MOVE * 0.85 : 0)) / 0.28, 0, 1);
if (a <= 0) continue;
p = geo.px(PTS[k]); var rr2 = geo.nr * pop(a);
if (k === ERR) { add(c, true); glow(c, P.sWarn, p[0], p[1], 64 + 8 * Math.sin(time * 3.2), 0.5); add(c, false); circle(c, p[0], p[1], rr2 + 5 + 1.5 * Math.sin(time * 3.2)); c.strokeStyle = col(P.warn, 0.75); c.lineWidth = 1.5; c.stroke(); }
circle(c, p[0], p[1], rr2);
if (k < ERR) { c.fillStyle = col(P.acc); c.fill(); }
else if (k === ERR) { c.fillStyle = col(P.warn); c.fill(); }
else { c.fillStyle = col(P.bg); c.fill(); c.strokeStyle = col(P.warn, 0.9); c.lineWidth = 1.6; c.stroke(); }
if (k === cur || k === hover) { circle(c, p[0], p[1], rr2 + 3.5); c.strokeStyle = col(P.t1, 0.95); c.lineWidth = 1.5; c.stroke(); }
c.font = '700 ' + (geo.nr < 10 ? 9.5 : 10.5) + 'px ' + FONT; c.fillStyle = k > ERR ? col(P.warn) : col(P.bg); c.globalAlpha = a; c.fillText(String(k + 1), p[0], p[1] + 0.5); c.globalAlpha = 1;
}
/* labels */
a = clamp((clock - starts[ERR] - MOVE) / 0.4, 0, 1);
if (a > 0) { p = geo.px(PTS[ERR]); label(c, 'first error', p[0], p[1] - geo.nr - 13, { align: 'center', size: 12.5, w: 700, color: P.warn, a: a }); }
a = clamp((clock - starts[7] - MOVE) / 0.5, 0, 1);
if (a > 0) label(c, 'later steps drift back', geo.W - 12, geo.top + (geo.H - geo.top - 8) * 0.965, { align: 'right', size: 11.5, a: a });
if (fade > 0) { c.globalAlpha = fade; c.drawImage(d.bgc, 0, 0, d.W, d.H); c.globalAlpha = 1; }
};
d.still = function () { clock = total + 0.01; fade = 0; sync(true); d.draw(); };
function seek(k) {
if (REDUCE) { pick = k; sync(true); d.draw(); return; }
clock = k === N - 1 ? total + 0.01 : starts[k] + MOVE + 0.35; pause = 4.5; phase = 0; fade = 0; sync(true);
}
d.act = function () { if (REDUCE) { pick = -1; d.still(); return; } clock = 0; pause = 0; phase = 0; fade = 0; sync(true); };
Array.prototype.forEach.call(lis, function (li, k) { li.addEventListener('click', function () { seek(k); }); });
function near(e) {
var m = d.pt(e), best = -1, bd = 18, k, p, dd;
for (k = 0; k < N; k++) { if (clock < starts[k]) break; p = geo.px(PTS[k]); dd = Math.hypot(m[0] - p[0], m[1] - p[1]); if (dd < bd) { bd = dd; best = k; } }
return best;
}
d.cv.addEventListener('pointermove', function (e) { if (!geo) return; var h = near(e); if (h !== hover) { hover = h; d.cv.style.cursor = h >= 0 ? 'pointer' : ''; if (!d.run) d.draw(); } });
d.cv.addEventListener('pointerleave', function () { if (hover >= 0) { hover = -1; if (!d.run) d.draw(); } });
d.cv.addEventListener('click', function (e) { if (!geo) return; var h = near(e); if (h >= 0) seek(h); });
if (document.fonts && document.fonts.ready) document.fonts.ready.then(function () { d.size(); d.paint(true); });
sync(true);
});
/* ================================================================
   3. Now change the model. Two detectors look at the same steps.
   Top: a schematic of the explanation in the post. A different model keeps the
   same structure in different coordinates. The teacher rebuilds its lens from
   the step labels, so its boundary follows. The student learned one boundary
   and keeps it. Positions are illustrative.
   Bottom: step-level AUROC from the paper, Tables 3 (teacher) and 4 (student).
   Bars are means over train and test pairs, dots are the pairs.
   ================================================================ */
demo('gx-shift', function (d) {
var el = d.el, cv2 = el.querySelectorAll('canvas')[1], c2 = cv2.getContext('2d');
var btns = el.querySelectorAll('.gxs-seg button'), vals = el.querySelectorAll('[data-v]'), tracks = el.querySelectorAll('.gxs-track');
var pos = el.querySelectorAll('.gxs-pos'), neg = el.querySelectorAll('.gxs-neg');
var LLM = ['Qwen', 'Llama', 'Mistral'];
/* rows: trained on. columns: tested on. order: Qwen, Llama, Mistral */
var AUROC = [
[[91.6, 91.7, 90.9], [90.7, 91.7, 91.2], [90.1, 90.6, 91.5]],
[[93.6, 39.1, 35.4], [51.5, 93.5, 33.4], [48.8, 58.5, 93.9]]
];
var PAIRS = [[0, 1], [0, 2], [1, 0], [1, 2], [2, 0], [2, 1]], LO = 30, SPAN = 70;
var mean = [], dots = [], k, j, i;
for (k = 0; k < 2; k++) {
var a = AUROC[k], diff = 0;
for (j = 0; j < 6; j++) diff += a[PAIRS[j][0]][PAIRS[j][1]] / 6;
mean.push([(a[0][0] + a[1][1] + a[2][2]) / 3, diff]);
dots.push([]);
for (j = 0; j < 6; j++) { var s = document.createElement('span'); s.className = 'gx-dot'; s.tabIndex = -1; tracks[k].appendChild(s); dots[k].push(s); }
}
/* the steps: a broad group of correct ones and a tighter group of wrong ones, with a gap between */
var PHI = -22 * Math.PI / 180, TURN = 97 * Math.PI / 180, pts = [], r = rng(23);
function tg(lim) { var g; do { g = gauss(r); } while (Math.abs(g) > lim); return g; }
for (i = 0; i < 62; i++) pts.push({ u: tg(2) * 0.27, n: -0.41 + tg(1.9) * 0.14, w: 0, ph: r() * 6.283 });
for (i = 0; i < 22; i++) pts.push({ u: tg(2) * 0.17, n: 0.44 + tg(1.9) * 0.11, w: 1, ph: r() * 6.283 });
/* no boundary is perfect: a few steps sit on the wrong side even on the model it was built for */
pts.push({ u: 0.21, n: 0.07, w: 0, ph: 1.1 }, { u: -0.3, n: 0.045, w: 0, ph: 4.2 }, { u: -0.08, n: -0.06, w: 1, ph: 2.6 });
var target = REDUCE ? 1 : 0, raw = target, m = target, auto = !REDUCE, timer = 0, time = 0, mk = '';
function seg() {
for (var b = 0; b < btns.length; b++) {
var on = (btns[b].getAttribute('data-act') === 'diff') === !!target;
btns[b].classList.toggle('on', on); btns[b].setAttribute('aria-pressed', on ? 'true' : 'false');
}
}
function meters(force) {
var key = Math.round(m * 2000) + '';
if (key === mk && !force) return;
mk = key;
for (var k = 0; k < 2; k++) {
var v = mean[k][0] + (mean[k][1] - mean[k][0]) * m;
vals[k].textContent = Math.round(v);
pos[k].style.width = (Math.max(0, v - 50) / SPAN * 100).toFixed(2) + '%';
neg[k].style.width = (Math.max(0, 50 - v) / SPAN * 100).toFixed(2) + '%';
for (var j = 0; j < 6; j++) {
var tr = PAIRS[j][0], te = m < 0.5 ? tr : PAIRS[j][1], a = AUROC[k][tr][tr], b = AUROC[k][tr][PAIRS[j][1]], x = a + (b - a) * m;
dots[k][j].style.left = ((x - LO) / SPAN * 100).toFixed(2) + '%';
dots[k][j].classList.toggle('r', x > 78);
dots[k][j].setAttribute('data-tip', LLM[tr] + ' → ' + LLM[te] + '  ' + AUROC[k][tr][te].toFixed(1));
}
}
}
d.heightFor = function (w) { return w < 260 ? 150 : clamp(Math.round(w * 0.48), 200, 224); };
var W2 = 0;
d.layout = function () {
cv2.style.height = d.H + 'px'; W2 = cv2.clientWidth || d.W;
cv2.width = Math.round(W2 * d.dpr); cv2.height = d.cv.height;
c2.setTransform(d.dpr, 0, 0, d.dpr, 0, 0);
};
/* one detector's view. k = 0: the boundary turns with the steps. k = 1: it stays where it was learned. */
function plot(c, k) {
var W = k ? W2 : d.W, H = d.H, cx = W / 2, cy = H / 2, s = Math.min(W, H) * 0.5 * 1.02, th = PHI + TURN * m, bn = k ? PHI : th;
var nx = Math.cos(bn), ny = Math.sin(bn), L = W + H, p, x, y, rad = W < 260 ? 2.1 : 2.6, wob = REDUCE ? 0 : 0.014;
c.globalCompositeOperation = 'source-over'; c.globalAlpha = 1; c.setLineDash([]);
c.drawImage(d.bgc, 0, 0, W, H);
/* what the detector flags: everything on one side of its boundary */
var gr = c.createLinearGradient(cx, cy, cx + nx * s * 1.5, cy + ny * s * 1.5);
gr.addColorStop(0, col(P.warn, 0.24)); gr.addColorStop(1, col(P.warn, 0.05));
c.beginPath();
c.moveTo(cx - ny * L, cy + nx * L); c.lineTo(cx + ny * L, cy - nx * L);
c.lineTo(cx + ny * L + nx * L, cy - nx * L + ny * L); c.lineTo(cx - ny * L + nx * L, cy + nx * L + ny * L);
c.closePath(); c.fillStyle = gr; c.fill();
c.beginPath(); c.moveTo(cx - ny * L, cy + nx * L); c.lineTo(cx + ny * L, cy - nx * L);
c.strokeStyle = col(P.t1, 0.9); c.lineWidth = 1.5; c.stroke();
/* the steps, in this model's coordinates */
var ct = Math.cos(th), st = Math.sin(th);
for (var i = 0; i < pts.length; i++) {
p = pts[i];
var n = p.n + Math.sin(time * 0.9 + p.ph) * wob, u = p.u + Math.cos(time * 0.7 + p.ph * 1.7) * wob;
x = cx + (n * ct - u * st) * s; y = cy + (n * st + u * ct) * s;
circle(c, x, y, (p.w ? rad + 0.4 : rad) + 1.3); c.fillStyle = col(P.bg, 0.55); c.fill();
circle(c, x, y, p.w ? rad + 0.4 : rad); c.fillStyle = p.w ? col(P.warn) : col(P.acc); c.fill();
}
}
d.step = function (dt) {
time += dt;
if (auto) { timer += dt; if (timer >= (target ? 5.6 : 3.2)) { target = 1 - target; timer = 0; seg(); } }
raw = clamp(raw + (target ? dt : -dt) / 1.5, 0, 1); m = ease(raw);
meters();
};
d.draw = function () { if (!d.W) return; plot(d.ctx, 0); plot(c2, 1); };
d.still = function () { raw = m = target; meters(true); d.draw(); };
d.act = function (name) { auto = false; target = name === 'diff' ? 1 : 0; seg(); };
seg(); meters(true);
});
/* ================================================================
   2. Same model, same data. A plain chart of the paper's Table 1. The bars are
   drawn by the stylesheet; this only makes them grow when the chart scrolls in.
   ================================================================ */
(function () {
var el = document.getElementById('gx-indomain');
if (!el || REDUCE || !('IntersectionObserver' in window)) return;
el.classList.add('gx-anim');
var io = new IntersectionObserver(function (en) { if (en[en.length - 1].isIntersecting) { el.classList.add('gx-in'); io.disconnect(); } }, { threshold: 0.3 });
io.observe(el);
})();
/* a tap on a result dot shows its label on touch screens */
Array.prototype.forEach.call(document.querySelectorAll('.gx-dot'), function (s) { s.addEventListener('click', function () { s.focus(); }); });
var rt;
window.addEventListener('resize', function () {
clearTimeout(rt);
rt = setTimeout(function () { demos.forEach(function (d) { d.size(); d.paint(); }); }, 150);
});
if ('MutationObserver' in window) {
new MutationObserver(function () { palette(); demos.forEach(function (d) { if (d.W) { makeBg(d); d.paint(); } }); })
.observe(DOC, { attributes: true, attributeFilter: ['data-theme'] });
}
})();
</script>
