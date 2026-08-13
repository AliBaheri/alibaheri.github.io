---
layout: post
title: why the geometry of reasoning might matter
date: 2026-08-13 09:00:00-0400
description: reasoning failures may show up not only as incorrect words, but as unusual movements in a model's internal representation
tags: reasoning llm optimal-transport interpretability
categories: research-notes
_styles: >
  .post-content { font-size: 1.06rem; line-height: 1.78; }
  .post-content p { margin-bottom: 1.35rem; }
  .post-content h2 {
    margin-top: 3rem; margin-bottom: 1rem; font-size: 1.32rem; font-weight: 700;
    padding-bottom: .45rem;
    border-bottom: 2px solid color-mix(in srgb, var(--global-theme-color) 30%, transparent);
  }
  .lede { font-size: 1.22rem; line-height: 1.6; font-weight: 400; }
  .lede strong { font-weight: 600; }
  .keyline {
    margin: 2.4rem 0; padding: 1.5rem 1.6rem; border-radius: 10px; text-align: center;
    background: linear-gradient(135deg,
      color-mix(in srgb, var(--global-theme-color) 12%, transparent),
      color-mix(in srgb, var(--global-theme-color) 4%, transparent));
    font-size: 1.5rem; font-weight: 700; line-height: 1.3;
    color: var(--global-theme-color); letter-spacing: -.01em;
  }
  .fig { margin: 2.6rem 0 1.4rem; text-align: center; }
  .fig svg { max-width: 100%; height: auto; color: var(--global-text-color); }
  .fig figcaption {
    font-size: .84rem; line-height: 1.5; color: var(--global-text-color-light);
    margin-top: .7rem; max-width: 34rem; margin-left: auto; margin-right: auto;
  }
  .shift { margin: 2rem 0; }
  .shift .q {
    display: flex; align-items: flex-start; gap: 1rem;
    padding: .95rem 1.15rem; border-radius: 8px; margin-bottom: .6rem;
    background: color-mix(in srgb, var(--global-text-color) 5%, transparent);
    font-size: 1.02rem; line-height: 1.5;
  }
  .shift .q.to {
    background: color-mix(in srgb, var(--global-theme-color) 11%, transparent);
    box-shadow: inset 3px 0 0 var(--global-theme-color);
  }
  .shift .lbl {
    flex: 0 0 2.6rem; font-size: .68rem; font-weight: 700; letter-spacing: .1em;
    text-transform: uppercase; color: var(--global-theme-color); padding-top: .28rem;
  }
  .takeaway {
    margin: 2.8rem 0 1.5rem; padding: 1.3rem 1.5rem; border-radius: 10px;
    border: 1px solid color-mix(in srgb, var(--global-theme-color) 35%, transparent);
    background: color-mix(in srgb, var(--global-theme-color) 4%, transparent);
    font-size: 1.06rem; line-height: 1.65;
  }
  .takeaway .tl {
    display: block; font-size: .7rem; font-weight: 700; letter-spacing: .12em;
    text-transform: uppercase; color: var(--global-theme-color); margin-bottom: .5rem;
  }
  .paper-note {
    margin-top: 2.8rem; padding: 1.1rem 1.3rem; border-radius: 8px; font-size: .92rem;
    line-height: 1.6;
    border: 1px dashed color-mix(in srgb, var(--global-text-color) 25%, transparent);
  }
  @media (max-width: 576px) {
    .keyline { font-size: 1.2rem; padding: 1.2rem 1rem; }
    .lede { font-size: 1.1rem; }
  }
---

<p class="lede" markdown="1">
When we talk about AI reasoning, we usually focus on the words a model produces: the
steps it writes down, the answer it gives, or whether those steps are correct.
**But there is another way to look at reasoning.**
</p>

Inside a language model, every step is represented by a large collection of numbers
called a hidden state. As the model moves from one reasoning step to the next, those
hidden states also move. You can imagine them tracing out a path through a very
high-dimensional space.

That gives us a surprisingly simple idea:

<div class="keyline">Reasoning may have a geometry.</div>

In a recent paper, GeoReason, we explore this perspective. Instead of looking only at
what a model says, we study how its internal representations move while it reasons. Our
experiments suggest that the moment a model first makes a reasoning mistake can
sometimes correspond to a noticeable change in that trajectory.

## Why might geometry be useful here?

Imagine someone walking along a trail. You do not need to understand every thought in
their head to notice that they have suddenly made a sharp turn, wandered far away from
the usual path, or started moving in an unusual direction.

Something similar may happen during model reasoning.

A correct chain of reasoning could occupy a relatively stable region of representation
space. When the model makes a bad assumption or takes an incorrect logical step, its
internal state may move away from the kinds of transitions we normally see during
correct reasoning.

<figure class="fig">
<svg viewBox="0 0 720 280" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="A reasoning trajectory: early steps stay inside a shaded band of coherent transitions, then one step breaks away and later steps travel further from the band.">
<path d="M40.0,120.0 L46.4,121.8 L52.8,123.5 L59.2,125.2 L65.6,126.9 L72.0,128.6 L78.4,130.2 L84.8,131.8 L91.2,133.3 L97.6,134.8 L104.0,136.2 L110.4,137.6 L116.8,138.8 L123.2,140.0 L129.6,141.0 L136.0,142.0 L142.4,142.9 L148.8,143.7 L155.2,144.4 L161.6,144.9 L168.0,145.4 L174.4,145.7 L180.8,145.9 L187.2,146.0 L193.6,146.0 L200.0,145.8 L206.4,145.6 L212.8,145.2 L219.2,144.7 L225.6,144.1 L232.0,143.4 L238.4,142.6 L244.8,141.7 L251.2,140.7 L257.6,139.6 L264.0,138.4 L270.4,137.1 L276.8,135.7 L283.2,134.3 L289.6,132.8 L296.0,131.2 L302.4,129.6 L308.8,128.0 L315.2,126.3 L321.6,124.6 L328.0,122.9 L334.4,121.1 L340.8,119.4 L347.2,117.6 L353.6,115.9 L360.0,114.2 L366.4,112.5 L372.8,110.8 L379.2,109.2 L385.6,107.6 L392.0,106.1 L398.4,104.7 L404.8,103.3 L411.2,102.0 L417.6,100.8 L424.0,99.6 L430.4,98.6 L436.8,97.6 L443.2,96.8 L449.6,96.1 L456.0,95.4 L462.4,94.9 L468.8,94.5 L475.2,94.2 L481.6,94.1 L488.0,94.0 L494.4,94.1 L500.8,94.2 L507.2,94.5 L513.6,95.0 L520.0,95.5 L526.4,96.1 L532.8,96.9 L539.2,97.7 L545.6,98.7 L552.0,99.7 L558.4,100.9 L564.8,102.1 L571.2,103.4 L577.6,104.8 L584.0,106.3 L590.4,107.8 L596.8,109.3 L603.2,111.0 L609.6,112.6 L616.0,114.3 L622.4,116.0 L628.8,117.8 L635.2,119.5 L641.6,121.3 L648.0,123.0 L654.4,124.8 L660.8,126.5 L667.2,128.2 L673.6,129.8 L680.0,131.4 L680.0,191.4 L673.6,189.8 L667.2,188.2 L660.8,186.5 L654.4,184.8 L648.0,183.0 L641.6,181.3 L635.2,179.5 L628.8,177.8 L622.4,176.0 L616.0,174.3 L609.6,172.6 L603.2,171.0 L596.8,169.3 L590.4,167.8 L584.0,166.3 L577.6,164.8 L571.2,163.4 L564.8,162.1 L558.4,160.9 L552.0,159.7 L545.6,158.7 L539.2,157.7 L532.8,156.9 L526.4,156.1 L520.0,155.5 L513.6,155.0 L507.2,154.5 L500.8,154.2 L494.4,154.1 L488.0,154.0 L481.6,154.1 L475.2,154.2 L468.8,154.5 L462.4,154.9 L456.0,155.4 L449.6,156.1 L443.2,156.8 L436.8,157.6 L430.4,158.6 L424.0,159.6 L417.6,160.8 L411.2,162.0 L404.8,163.3 L398.4,164.7 L392.0,166.1 L385.6,167.6 L379.2,169.2 L372.8,170.8 L366.4,172.5 L360.0,174.2 L353.6,175.9 L347.2,177.6 L340.8,179.4 L334.4,181.1 L328.0,182.9 L321.6,184.6 L315.2,186.3 L308.8,188.0 L302.4,189.6 L296.0,191.2 L289.6,192.8 L283.2,194.3 L276.8,195.7 L270.4,197.1 L264.0,198.4 L257.6,199.6 L251.2,200.7 L244.8,201.7 L238.4,202.6 L232.0,203.4 L225.6,204.1 L219.2,204.7 L212.8,205.2 L206.4,205.6 L200.0,205.8 L193.6,206.0 L187.2,206.0 L180.8,205.9 L174.4,205.7 L168.0,205.4 L161.6,204.9 L155.2,204.4 L148.8,203.7 L142.4,202.9 L136.0,202.0 L129.6,201.0 L123.2,200.0 L116.8,198.8 L110.4,197.6 L104.0,196.2 L97.6,194.8 L91.2,193.3 L84.8,191.8 L78.4,190.2 L72.0,188.6 L65.6,186.9 L59.2,185.2 L52.8,183.5 L46.4,181.8 L40.0,180.0 Z" fill="var(--global-theme-color)" fill-opacity=".10"/>
<path d="M40.0,120.0 L46.4,121.8 L52.8,123.5 L59.2,125.2 L65.6,126.9 L72.0,128.6 L78.4,130.2 L84.8,131.8 L91.2,133.3 L97.6,134.8 L104.0,136.2 L110.4,137.6 L116.8,138.8 L123.2,140.0 L129.6,141.0 L136.0,142.0 L142.4,142.9 L148.8,143.7 L155.2,144.4 L161.6,144.9 L168.0,145.4 L174.4,145.7 L180.8,145.9 L187.2,146.0 L193.6,146.0 L200.0,145.8 L206.4,145.6 L212.8,145.2 L219.2,144.7 L225.6,144.1 L232.0,143.4 L238.4,142.6 L244.8,141.7 L251.2,140.7 L257.6,139.6 L264.0,138.4 L270.4,137.1 L276.8,135.7 L283.2,134.3 L289.6,132.8 L296.0,131.2 L302.4,129.6 L308.8,128.0 L315.2,126.3 L321.6,124.6 L328.0,122.9 L334.4,121.1 L340.8,119.4 L347.2,117.6 L353.6,115.9 L360.0,114.2 L366.4,112.5 L372.8,110.8 L379.2,109.2 L385.6,107.6 L392.0,106.1 L398.4,104.7 L404.8,103.3 L411.2,102.0 L417.6,100.8 L424.0,99.6 L430.4,98.6 L436.8,97.6 L443.2,96.8 L449.6,96.1 L456.0,95.4 L462.4,94.9 L468.8,94.5 L475.2,94.2 L481.6,94.1 L488.0,94.0 L494.4,94.1 L500.8,94.2 L507.2,94.5 L513.6,95.0 L520.0,95.5 L526.4,96.1 L532.8,96.9 L539.2,97.7 L545.6,98.7 L552.0,99.7 L558.4,100.9 L564.8,102.1 L571.2,103.4 L577.6,104.8 L584.0,106.3 L590.4,107.8 L596.8,109.3 L603.2,111.0 L609.6,112.6 L616.0,114.3 L622.4,116.0 L628.8,117.8 L635.2,119.5 L641.6,121.3 L648.0,123.0 L654.4,124.8 L660.8,126.5 L667.2,128.2 L673.6,129.8 L680.0,131.4 L680.0,191.4 L673.6,189.8 L667.2,188.2 L660.8,186.5 L654.4,184.8 L648.0,183.0 L641.6,181.3 L635.2,179.5 L628.8,177.8 L622.4,176.0 L616.0,174.3 L609.6,172.6 L603.2,171.0 L596.8,169.3 L590.4,167.8 L584.0,166.3 L577.6,164.8 L571.2,163.4 L564.8,162.1 L558.4,160.9 L552.0,159.7 L545.6,158.7 L539.2,157.7 L532.8,156.9 L526.4,156.1 L520.0,155.5 L513.6,155.0 L507.2,154.5 L500.8,154.2 L494.4,154.1 L488.0,154.0 L481.6,154.1 L475.2,154.2 L468.8,154.5 L462.4,154.9 L456.0,155.4 L449.6,156.1 L443.2,156.8 L436.8,157.6 L430.4,158.6 L424.0,159.6 L417.6,160.8 L411.2,162.0 L404.8,163.3 L398.4,164.7 L392.0,166.1 L385.6,167.6 L379.2,169.2 L372.8,170.8 L366.4,172.5 L360.0,174.2 L353.6,175.9 L347.2,177.6 L340.8,179.4 L334.4,181.1 L328.0,182.9 L321.6,184.6 L315.2,186.3 L308.8,188.0 L302.4,189.6 L296.0,191.2 L289.6,192.8 L283.2,194.3 L276.8,195.7 L270.4,197.1 L264.0,198.4 L257.6,199.6 L251.2,200.7 L244.8,201.7 L238.4,202.6 L232.0,203.4 L225.6,204.1 L219.2,204.7 L212.8,205.2 L206.4,205.6 L200.0,205.8 L193.6,206.0 L187.2,206.0 L180.8,205.9 L174.4,205.7 L168.0,205.4 L161.6,204.9 L155.2,204.4 L148.8,203.7 L142.4,202.9 L136.0,202.0 L129.6,201.0 L123.2,200.0 L116.8,198.8 L110.4,197.6 L104.0,196.2 L97.6,194.8 L91.2,193.3 L84.8,191.8 L78.4,190.2 L72.0,188.6 L65.6,186.9 L59.2,185.2 L52.8,183.5 L46.4,181.8 L40.0,180.0 Z" fill="none" stroke="var(--global-theme-color)" stroke-opacity=".30" stroke-width="1" stroke-dasharray="4 4"/>
<path d="M70.0,164.1 L130.0,163.1 L190.0,180.0 L250.0,165.9 L310.0,164.7 L370.0,138.5" fill="none" stroke="var(--global-theme-color)" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M370.0,138.5 L430.0,81.8 L490.0,44.8 L550.0,-3.8 L610.0,-66.1" fill="none" stroke="#d97706" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="7 5"/>
<circle cx="70.0" cy="164.1" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="130.0" cy="163.1" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="190.0" cy="180.0" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="250.0" cy="165.9" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="310.0" cy="164.7" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="370.0" cy="138.5" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="430.0" cy="81.8" r="7.5" fill="none" stroke="#d97706" stroke-width="2"/>
<circle cx="430.0" cy="81.8" r="4.6" fill="#d97706"/>
<circle cx="490.0" cy="44.8" r="4.6" fill="#d97706" fill-opacity=".55"/>
<circle cx="550.0" cy="-3.8" r="4.6" fill="#d97706" fill-opacity=".55"/>
<circle cx="610.0" cy="-66.1" r="4.6" fill="#d97706" fill-opacity=".55"/>
<line x1="430.0" y1="67.8" x2="430.0" y2="43.8" stroke="#d97706" stroke-width="1.2"/>
<text x="430.0" y="35.8" text-anchor="middle" font-size="13" font-weight="700" fill="#d97706">first error</text>
<text x="60" y="219" font-size="12.5" fill="var(--global-theme-color)" font-weight="600">band of coherent transitions</text>
<text x="690" y="46" text-anchor="end" font-size="12.5" fill="#d97706" font-weight="600">excursion</text>
<text x="40" y="268" font-size="11.5" fill="currentColor" fill-opacity=".55">reasoning step &#8594;</text>
</svg>
<figcaption>Each dot is one reasoning step. While the chain holds together, the steps stay
inside a band of transitions that look like the ones we see when reasoning goes well. A
first error shows up as a departure from that band &mdash; and once the trajectory leaves,
later steps travel further still.</figcaption>
</figure>

The important point is that this gives us information that is different from simply
looking at the text.

A model can produce a sentence that sounds completely confident and reasonable while
still taking a wrong step. The language may look smooth even when the underlying
reasoning process has changed.

Geometry gives us another signal: not just what the model is saying, but how its
internal reasoning state is moving.

## A different question to ask

We find this especially interesting because it shifts the question from:

<div class="shift">
<div class="q"><span class="lbl">from</span><span>&ldquo;Does this sentence look wrong?&rdquo;</span></div>
<div class="q to"><span class="lbl">to</span><span>&ldquo;Does this reasoning step behave like the steps we usually see when reasoning is going well?&rdquo;</span></div>
</div>

There are still major challenges. A geometric signal that is easy to discover in
experiments is not automatically a reliable detector that works across every model and
every task. GeoReason itself shows that this generalization problem is far from solved.

But the broader idea feels promising.

If reasoning is a process, then perhaps we should study its dynamics, not only its
outputs. Mistakes may appear not only as incorrect words, but as unusual movements,
turns, or departures in a model's internal representation.

<div class="takeaway" markdown="1">
<span class="tl">The takeaway</span>
Understanding reasoning might require us to look not just at where a model ends up, but
at the path it takes to get there.
</div>

<div class="paper-note" markdown="1">
**The paper:** *Where Does Reasoning Break? Step-Level Hallucination Detection via
Hidden-State Transport Geometry* &mdash; available on
[arXiv](https://arxiv.org/abs/2605.13772){:target="_blank"}.
</div>
