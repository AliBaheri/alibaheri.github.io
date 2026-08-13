---
layout: post
title: why the geometry of reasoning might matter
date: 2026-08-12 09:00:00-0400
description: reasoning failures may show up not only as incorrect words, but as unusual movements in a model's internal representation
tags: reasoning llm optimal-transport interpretability
categories: research-notes
_styles: >
  .post-content h2 { margin-top: 2.4rem; font-size: 1.3rem; }
  .keyline {
    margin: 1.8rem 0; padding: .9rem 1.2rem; border-radius: 8px;
    border-left: 3px solid var(--global-theme-color);
    background: color-mix(in srgb, var(--global-theme-color) 5%, transparent);
    font-size: 1.05rem; font-weight: 600;
  }
  .shift { margin: 1.8rem 0; }
  .shift .q {
    display: flex; align-items: baseline; gap: .8rem;
    padding: .6rem .9rem; border-radius: 6px; margin-bottom: .5rem;
    background: color-mix(in srgb, var(--global-text-color) 5%, transparent);
    font-size: .98rem;
  }
  .shift .q.to { background: color-mix(in srgb, var(--global-theme-color) 9%, transparent); }
  .shift .lbl {
    flex: 0 0 auto; font-size: .68rem; font-weight: 700; letter-spacing: .08em;
    text-transform: uppercase; color: var(--global-theme-color); padding-top: .18rem;
  }
  .paper-note {
    margin-top: 2.6rem; padding: 1rem 1.2rem; border-radius: 8px; font-size: .9rem;
    border: 1px dashed color-mix(in srgb, var(--global-text-color) 25%, transparent);
  }
---

When we talk about AI reasoning, we usually focus on the words a model produces: the
steps it writes down, the answer it gives, or whether those steps are correct.

But there is another way to look at reasoning.

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

In other words, understanding reasoning might require us to look not just at where a
model ends up, but at the path it takes to get there.

<div class="paper-note" markdown="1">
**The paper:** *Where Does Reasoning Break? Step-Level Hallucination Detection via
Hidden-State Transport Geometry* &mdash; available on
[arXiv](https://arxiv.org/abs/2605.13772){:target="_blank"}.
</div>
