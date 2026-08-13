---
layout: post
title: Why the geometry of LLMs reasoning might matter?
date: 2026-06-15 09:00:00-0400
description: a wrong reasoning step can read perfectly well; it may still move differently
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
  .lede { font-size: 1.2rem; line-height: 1.62; }
  .keyline {
    margin: 2.4rem 0; padding: 1.5rem 1.6rem; border-radius: 10px; text-align: center;
    background: linear-gradient(135deg,
      color-mix(in srgb, var(--global-theme-color) 12%, transparent),
      color-mix(in srgb, var(--global-theme-color) 4%, transparent));
    font-size: 1.5rem; font-weight: 700; line-height: 1.3;
    color: var(--global-theme-color); letter-spacing: -.01em;
  }
  .fig { margin: 2.6rem 0 1.6rem; text-align: center; }
  .fig svg { max-width: 100%; height: auto; color: var(--global-text-color); }
  .fig figcaption {
    font-size: .84rem; line-height: 1.55; color: var(--global-text-color-light);
    margin-top: .8rem; max-width: 36rem; margin-left: auto; margin-right: auto; text-align: left;
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
    .keyline { font-size: 1.18rem; padding: 1.2rem 1rem; }
    .lede { font-size: 1.08rem; }
  }
---

<p class="lede" markdown="1">
A model is working through a problem. At step four it carries a quantity across
incorrectly &mdash; nothing dramatic, no confusion, just a small wrong turn. Steps five
through nine build on it, fluently and confidently. The final answer is wrong.
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
unlucky &mdash; it is measuring the wrong quantity.

Which raises the obvious question: is there somewhere else to look?

## Reasoning as a path

Inside a language model, every step is represented by a large collection of numbers
called a hidden state. As the model moves from one step to the next, those states move
too. A chain of reasoning traces a path through a very high-dimensional space.

<div class="keyline">Reasoning has a geometry.</div>

That path is what we studied in GeoReason.

The premise is a claim about *motion*, not location. Correct reasoning ranges widely
&mdash; it has to, since it covers different territory as it goes. What stays regular is
the step-to-step transition: the kind of move that follows from a given prefix belongs to
a comparatively narrow family. A first error is a move outside that family. It shows up
as a localized departure &mdash; an excursion &mdash; and once the trajectory has left,
later steps tend to travel further out.

<figure class="fig">
<svg viewBox="0 0 720 330" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Two panels of the same reasoning chain. In the text, every step looks uniformly fluent and nothing marks the error. In representation space, the steps stay inside a band of coherent transitions until one step departs and later steps travel further away.">
<text x="40" y="34" font-size="12" font-weight="700" letter-spacing="1.4" fill="currentColor" fill-opacity=".55">IN THE TEXT</text>
<text x="40" y="52" font-size="12.5" fill="currentColor" fill-opacity=".45">every step reads fluently &#8212; nothing marks the error</text>
<line x1="40" y1="78" x2="680" y2="78" stroke="currentColor" stroke-opacity=".28" stroke-width="2"/>
<circle cx="70.0" cy="78.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="130.0" cy="75.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="190.0" cy="80.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="250.0" cy="76.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="310.0" cy="81.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="370.0" cy="77.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="430.0" cy="79.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="490.0" cy="76.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="550.0" cy="80.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<circle cx="610.0" cy="77.0" r="4.4" fill="currentColor" fill-opacity=".38"/>
<line x1="40" y1="120" x2="680" y2="120" stroke="currentColor" stroke-opacity=".13" stroke-width="1"/>
<text x="40" y="150" font-size="12" font-weight="700" letter-spacing="1.4" fill="var(--global-theme-color)">IN REPRESENTATION SPACE</text>
<path d="M40.0,209.0 L46.4,210.3 L52.8,211.7 L59.2,213.0 L65.6,214.3 L72.0,215.6 L78.4,216.9 L84.8,218.1 L91.2,219.3 L97.6,220.4 L104.0,221.5 L110.4,222.5 L116.8,223.5 L123.2,224.4 L129.6,225.2 L136.0,225.9 L142.4,226.6 L148.8,227.2 L155.2,227.7 L161.6,228.2 L168.0,228.5 L174.4,228.8 L180.8,228.9 L187.2,229.0 L193.6,229.0 L200.0,228.9 L206.4,228.7 L212.8,228.4 L219.2,228.0 L225.6,227.6 L232.0,227.0 L238.4,226.4 L244.8,225.7 L251.2,224.9 L257.6,224.0 L264.0,223.1 L270.4,222.1 L276.8,221.1 L283.2,220.0 L289.6,218.8 L296.0,217.6 L302.4,216.4 L308.8,215.1 L315.2,213.8 L321.6,212.5 L328.0,211.2 L334.4,209.9 L340.8,208.5 L347.2,207.2 L353.6,205.8 L360.0,204.5 L366.4,203.2 L372.8,201.9 L379.2,200.7 L385.6,199.5 L392.0,198.3 L398.4,197.2 L404.8,196.1 L411.2,195.1 L417.6,194.2 L424.0,193.3 L430.4,192.5 L436.8,191.8 L443.2,191.2 L449.6,190.6 L456.0,190.1 L462.4,189.7 L468.8,189.4 L475.2,189.2 L481.6,189.0 L488.0,189.0 L494.4,189.1 L500.8,189.2 L507.2,189.4 L513.6,189.7 L520.0,190.1 L526.4,190.6 L532.8,191.2 L539.2,191.9 L545.6,192.6 L552.0,193.4 L558.4,194.3 L564.8,195.2 L571.2,196.2 L577.6,197.3 L584.0,198.4 L590.4,199.6 L596.8,200.8 L603.2,202.1 L609.6,203.3 L616.0,204.6 L622.4,206.0 L628.8,207.3 L635.2,208.6 L641.6,210.0 L648.0,211.3 L654.4,212.7 L660.8,214.0 L667.2,215.3 L673.6,216.5 L680.0,217.8 L680.0,269.8 L673.6,268.5 L667.2,267.3 L660.8,266.0 L654.4,264.7 L648.0,263.3 L641.6,262.0 L635.2,260.6 L628.8,259.3 L622.4,258.0 L616.0,256.6 L609.6,255.3 L603.2,254.1 L596.8,252.8 L590.4,251.6 L584.0,250.4 L577.6,249.3 L571.2,248.2 L564.8,247.2 L558.4,246.3 L552.0,245.4 L545.6,244.6 L539.2,243.9 L532.8,243.2 L526.4,242.6 L520.0,242.1 L513.6,241.7 L507.2,241.4 L500.8,241.2 L494.4,241.1 L488.0,241.0 L481.6,241.0 L475.2,241.2 L468.8,241.4 L462.4,241.7 L456.0,242.1 L449.6,242.6 L443.2,243.2 L436.8,243.8 L430.4,244.5 L424.0,245.3 L417.6,246.2 L411.2,247.1 L404.8,248.1 L398.4,249.2 L392.0,250.3 L385.6,251.5 L379.2,252.7 L372.8,253.9 L366.4,255.2 L360.0,256.5 L353.6,257.8 L347.2,259.2 L340.8,260.5 L334.4,261.9 L328.0,263.2 L321.6,264.5 L315.2,265.8 L308.8,267.1 L302.4,268.4 L296.0,269.6 L289.6,270.8 L283.2,272.0 L276.8,273.1 L270.4,274.1 L264.0,275.1 L257.6,276.0 L251.2,276.9 L244.8,277.7 L238.4,278.4 L232.0,279.0 L225.6,279.6 L219.2,280.0 L212.8,280.4 L206.4,280.7 L200.0,280.9 L193.6,281.0 L187.2,281.0 L180.8,280.9 L174.4,280.8 L168.0,280.5 L161.6,280.2 L155.2,279.7 L148.8,279.2 L142.4,278.6 L136.0,277.9 L129.6,277.2 L123.2,276.4 L116.8,275.5 L110.4,274.5 L104.0,273.5 L97.6,272.4 L91.2,271.3 L84.8,270.1 L78.4,268.9 L72.0,267.6 L65.6,266.3 L59.2,265.0 L52.8,263.7 L46.4,262.3 L40.0,261.0 Z" fill="var(--global-theme-color)" fill-opacity=".10"/>
<path d="M40.0,209.0 L46.4,210.3 L52.8,211.7 L59.2,213.0 L65.6,214.3 L72.0,215.6 L78.4,216.9 L84.8,218.1 L91.2,219.3 L97.6,220.4 L104.0,221.5 L110.4,222.5 L116.8,223.5 L123.2,224.4 L129.6,225.2 L136.0,225.9 L142.4,226.6 L148.8,227.2 L155.2,227.7 L161.6,228.2 L168.0,228.5 L174.4,228.8 L180.8,228.9 L187.2,229.0 L193.6,229.0 L200.0,228.9 L206.4,228.7 L212.8,228.4 L219.2,228.0 L225.6,227.6 L232.0,227.0 L238.4,226.4 L244.8,225.7 L251.2,224.9 L257.6,224.0 L264.0,223.1 L270.4,222.1 L276.8,221.1 L283.2,220.0 L289.6,218.8 L296.0,217.6 L302.4,216.4 L308.8,215.1 L315.2,213.8 L321.6,212.5 L328.0,211.2 L334.4,209.9 L340.8,208.5 L347.2,207.2 L353.6,205.8 L360.0,204.5 L366.4,203.2 L372.8,201.9 L379.2,200.7 L385.6,199.5 L392.0,198.3 L398.4,197.2 L404.8,196.1 L411.2,195.1 L417.6,194.2 L424.0,193.3 L430.4,192.5 L436.8,191.8 L443.2,191.2 L449.6,190.6 L456.0,190.1 L462.4,189.7 L468.8,189.4 L475.2,189.2 L481.6,189.0 L488.0,189.0 L494.4,189.1 L500.8,189.2 L507.2,189.4 L513.6,189.7 L520.0,190.1 L526.4,190.6 L532.8,191.2 L539.2,191.9 L545.6,192.6 L552.0,193.4 L558.4,194.3 L564.8,195.2 L571.2,196.2 L577.6,197.3 L584.0,198.4 L590.4,199.6 L596.8,200.8 L603.2,202.1 L609.6,203.3 L616.0,204.6 L622.4,206.0 L628.8,207.3 L635.2,208.6 L641.6,210.0 L648.0,211.3 L654.4,212.7 L660.8,214.0 L667.2,215.3 L673.6,216.5 L680.0,217.8 L680.0,269.8 L673.6,268.5 L667.2,267.3 L660.8,266.0 L654.4,264.7 L648.0,263.3 L641.6,262.0 L635.2,260.6 L628.8,259.3 L622.4,258.0 L616.0,256.6 L609.6,255.3 L603.2,254.1 L596.8,252.8 L590.4,251.6 L584.0,250.4 L577.6,249.3 L571.2,248.2 L564.8,247.2 L558.4,246.3 L552.0,245.4 L545.6,244.6 L539.2,243.9 L532.8,243.2 L526.4,242.6 L520.0,242.1 L513.6,241.7 L507.2,241.4 L500.8,241.2 L494.4,241.1 L488.0,241.0 L481.6,241.0 L475.2,241.2 L468.8,241.4 L462.4,241.7 L456.0,242.1 L449.6,242.6 L443.2,243.2 L436.8,243.8 L430.4,244.5 L424.0,245.3 L417.6,246.2 L411.2,247.1 L404.8,248.1 L398.4,249.2 L392.0,250.3 L385.6,251.5 L379.2,252.7 L372.8,253.9 L366.4,255.2 L360.0,256.5 L353.6,257.8 L347.2,259.2 L340.8,260.5 L334.4,261.9 L328.0,263.2 L321.6,264.5 L315.2,265.8 L308.8,267.1 L302.4,268.4 L296.0,269.6 L289.6,270.8 L283.2,272.0 L276.8,273.1 L270.4,274.1 L264.0,275.1 L257.6,276.0 L251.2,276.9 L244.8,277.7 L238.4,278.4 L232.0,279.0 L225.6,279.6 L219.2,280.0 L212.8,280.4 L206.4,280.7 L200.0,280.9 L193.6,281.0 L187.2,281.0 L180.8,280.9 L174.4,280.8 L168.0,280.5 L161.6,280.2 L155.2,279.7 L148.8,279.2 L142.4,278.6 L136.0,277.9 L129.6,277.2 L123.2,276.4 L116.8,275.5 L110.4,274.5 L104.0,273.5 L97.6,272.4 L91.2,271.3 L84.8,270.1 L78.4,268.9 L72.0,267.6 L65.6,266.3 L59.2,265.0 L52.8,263.7 L46.4,262.3 L40.0,261.0 Z" fill="none" stroke="var(--global-theme-color)" stroke-opacity=".28" stroke-width="1" stroke-dasharray="4 4"/>
<path d="M70.0,246.2 L130.0,244.2 L190.0,258.0 L250.0,247.0 L310.0,246.9 L370.0,226.5" fill="none" stroke="var(--global-theme-color)" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/>
<path d="M370.0,226.5 L430.0,178.2 L490.0,146.6 L550.0,104.0 L610.0,48.8" fill="none" stroke="#d97706" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round" stroke-dasharray="7 5"/>
<circle cx="70.0" cy="246.2" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="130.0" cy="244.2" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="190.0" cy="258.0" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="250.0" cy="247.0" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="310.0" cy="246.9" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="370.0" cy="226.5" r="4.6" fill="var(--global-theme-color)"/>
<circle cx="430.0" cy="178.2" r="7.6" fill="none" stroke="#d97706" stroke-width="2"/>
<circle cx="430.0" cy="178.2" r="4.6" fill="#d97706"/>
<circle cx="490.0" cy="146.6" r="4.6" fill="#d97706" fill-opacity=".5"/>
<circle cx="550.0" cy="104.0" r="4.6" fill="#d97706" fill-opacity=".5"/>
<circle cx="610.0" cy="48.8" r="4.6" fill="#d97706" fill-opacity=".5"/>
<line x1="430" y1="89" x2="430" y2="164.22417694325506" stroke="#d97706" stroke-opacity=".45" stroke-width="1.2" stroke-dasharray="3 4"/>
<text x="442" y="109" font-size="12" font-weight="600" fill="#d97706">same step</text>
<text x="430" y="156.22417694325506" text-anchor="middle" font-size="13" font-weight="700" fill="#d97706">first error</text>
<text x="680" y="296" text-anchor="end" font-size="12" fill="var(--global-theme-color)" font-weight="600">band of coherent transitions</text>
<text x="40" y="320" font-size="11.5" fill="currentColor" fill-opacity=".5">reasoning step &#8594;</text>
</svg>
<figcaption>The same reasoning chain, seen two ways. Read as text, every step is equally
fluent and the error leaves no trace. Seen as a trajectory, the steps hold inside a band
of coherent transitions until one of them breaks away.</figcaption>
</figure>

The everyday version of this: you do not need to read someone's mind to notice they have
walked off the trail.

## The part that surprised us

It would be tidy to stop there. The more useful result is the one that complicates it.

We built two detectors. A **teacher** uses step labels to construct a contrastive
geometric lens and score how unstable each transition is. It is accurate, but it is not
deployable &mdash; at deployment you do not have labels. So we distilled it into a
**student** that scores raw hidden states in a single pass, with no labels at all.

In-domain, both beat entropy-based, probing-based, and attention-based baselines. Then we
changed the model and changed the dataset. The teacher held up. The student collapsed.

That gap is the finding worth carrying out of the paper. The teacher's transfer says the
geometric signal is not an artifact of one model or one benchmark &mdash; the structure
is shared. What fails to transfer is the *decision boundary*. The margin separating
coherent transitions from excursions shifts when the distribution shifts, and a student
that has learned where the boundary sat no longer finds it.

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

<div class="takeaway" markdown="1">
<span class="tl">The takeaway</span>
Understanding reasoning may require looking not just at where a model ends up, but at the
path it took &mdash; and at the point where that path turned.
</div>

<div class="paper-note" markdown="1">
**The paper:** *Where Does Reasoning Break? Step-Level Hallucination Detection via
Hidden-State Transport Geometry* &mdash; available on
[arXiv](https://arxiv.org/abs/2605.13772){:target="_blank"}. The geometry we use to
measure those departures comes from optimal transport, a thread that runs through much of
our [research](/research/).
</div>
