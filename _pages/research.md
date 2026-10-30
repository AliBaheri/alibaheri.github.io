---
layout: page
permalink: /research/
title: research
description: Physical AI that can be trusted &mdash; learned dynamics, safe decision-making, and calibrated uncertainty for aircraft, robots, and autonomous vehicles.
nav: true
nav_order: 1
---

<!-- Plain HTML on purpose: no Jekyll plugins required, so this builds on
     GitHub Pages with no extra setup.
     To add a paper to a theme, copy one list item inside that theme's
     papers list and edit the venue, title, link, and year.
     To reorder themes, move the whole block and renumber. -->

<style>
/* ---------- intro ---------- */
.rintro {
  font-size: 1.02rem; line-height: 1.68; margin-bottom: 1.8rem;
  padding-left: 1.1rem; border-left: 3px solid var(--global-theme-color);
}

/* ---------- overview cards ---------- */
.tgrid {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: .85rem; margin: 0 0 3.4rem;
}
a.tcard {
  display: block; padding: 1.1rem 1rem 1rem; border-radius: 10px;
  text-decoration: none !important; color: var(--global-text-color) !important;
  border: 1px solid color-mix(in srgb, var(--global-text-color) 14%, transparent);
  background: color-mix(in srgb, var(--global-theme-color) 3%, transparent);
  transition: transform .2s ease, box-shadow .2s ease, border-color .2s ease;
}
a.tcard:hover {
  transform: translateY(-3px);
  border-color: var(--global-theme-color);
  box-shadow: 0 8px 22px color-mix(in srgb, var(--global-theme-color) 22%, transparent);
}
a.tcard .ci { font-size: 1.45rem; color: var(--global-theme-color); line-height: 1; }
a.tcard .cn {
  font-size: .66rem; letter-spacing: .14em; font-weight: 700; margin-top: .7rem;
  color: color-mix(in srgb, var(--global-theme-color) 75%, var(--global-text-color));
}
a.tcard .ct { font-size: .94rem; font-weight: 600; line-height: 1.32; margin-top: .12rem; }
a.tcard .cc { font-size: .72rem; color: var(--global-text-color-light); margin-top: .5rem; }

/* ---------- theme sections ---------- */
.theme { position: relative; margin-bottom: 3.6rem; scroll-margin-top: 5rem; }
.theme .watermark {
  position: absolute; right: 0; top: -1.2rem;
  font-size: 5rem; font-weight: 800; line-height: 1;
  color: color-mix(in srgb, var(--global-theme-color) 10%, transparent);
  pointer-events: none; user-select: none; z-index: 0;
}
.theme .thead {
  display: flex; align-items: center; gap: .8rem;
  margin-bottom: .9rem; position: relative; z-index: 1;
}
.theme .ticon {
  flex: 0 0 auto; width: 2.7rem; height: 2.7rem; border-radius: 12px;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.1rem; color: #fff;
  background: var(--global-theme-color);
  background: linear-gradient(135deg, var(--global-theme-color),
    color-mix(in srgb, var(--global-theme-color) 58%, #000));
  box-shadow: 0 3px 10px color-mix(in srgb, var(--global-theme-color) 34%, transparent);
}
.theme .ttitle { margin: 0; font-size: 1.28rem; line-height: 1.28; }
.theme .tsub {
  font-size: .75rem; text-transform: uppercase; letter-spacing: .07em;
  color: var(--global-theme-color); margin-top: .18rem;
}
.theme .tbody { font-size: .95rem; line-height: 1.68; margin-bottom: 1.15rem; position: relative; z-index: 1; }

/* ---------- paper lists ---------- */
.theme .papers { list-style: none; padding: 0; margin: 0; }
.theme .papers li {
  display: flex; align-items: baseline; gap: .7rem;
  padding: .44rem .5rem .44rem .55rem; border-radius: 4px;
  border-top: 1px solid color-mix(in srgb, var(--global-text-color) 11%, transparent);
  font-size: .88rem; transition: background .18s ease;
}
.theme .papers li:last-child {
  border-bottom: 1px solid color-mix(in srgb, var(--global-text-color) 11%, transparent);
}
.theme .papers li:hover { background: color-mix(in srgb, var(--global-theme-color) 8%, transparent); }
.theme .papers .pv {
  flex: 0 0 4.7rem; font-size: .71rem; font-weight: 700;
  color: var(--global-theme-color); text-transform: uppercase; letter-spacing: .03em;
}
.theme .papers .pt { flex: 1; }
.theme .papers .py { flex: 0 0 auto; font-size: .78rem; color: var(--global-text-color-light); }

/* ---------- funding ---------- */
.rfund { margin-top: 3.4rem; }
.rfund ul { list-style: none; padding: 0; }
.rfund li {
  padding: .52rem 0 .52rem .95rem; font-size: .9rem; margin-bottom: .45rem;
  border-left: 2px solid color-mix(in srgb, var(--global-theme-color) 42%, transparent);
}
.rfund .agency { font-weight: 600; color: var(--global-theme-color); }
.rfund .role { font-size: .78rem; color: var(--global-text-color-light); }

@media (max-width: 576px) {
  .theme .watermark { font-size: 3.4rem; top: -.7rem; }
  .theme .papers li { flex-wrap: wrap; gap: .3rem .6rem; }
  .theme .papers .pv { flex: 0 0 auto; }
}
@media (prefers-reduced-motion: reduce) {
  a.tcard, a.tcard:hover, .theme .papers li { transition: none; transform: none; }
}

/* ---------- live demos ---------- */
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
/* ---------- concept figure (safe RL) ---------- */
.demo-tag {
  display: inline-flex; align-items: center; padding: .12rem .55rem; border-radius: 999px;
  font-size: .6rem; font-weight: 700; letter-spacing: .14em; text-transform: uppercase; color: var(--dm-acc);
  background: color-mix(in srgb, var(--dm-acc) 14%, transparent);
}
.demo-cite { font-variant-numeric: normal; }
.demo-fig .fig {
  --dm-warn: #e0911f;
  padding: .7rem .5rem .4rem;
  background: radial-gradient(ellipse 70% 60% at 50% 42%, color-mix(in srgb, var(--dm-acc) 13%, transparent), transparent 72%),
  radial-gradient(rgba(255, 255, 255, .075) 1px, transparent 1.3px) 11px 11px / 22px 22px;
}
.demo-fig svg { display: block; width: 100%; height: auto; font-family: inherit; overflow: visible; }
.demo-fig svg.ft2 { display: none; max-width: 370px; margin: 0 auto; }
@media (max-width: 620px) { .demo-fig svg.fw { display: none; } .demo-fig svg.ft2 { display: block; } }
.demo-fig .gc { stroke-width: 1.4; }
.demo-fig .gc.acc { fill: color-mix(in srgb, var(--dm-acc) 14%, var(--dm-bg)); stroke: var(--dm-acc); }
.demo-fig .gc.hum { fill: color-mix(in srgb, var(--dm-warn) 14%, var(--dm-bg)); stroke: var(--dm-warn); }
.demo-fig .gi { fill: none; stroke-width: 1.7; stroke-linecap: round; stroke-linejoin: round; }
.demo-fig .gi.acc { stroke: var(--dm-acc); }
.demo-fig .gi.hum { stroke: var(--dm-warn); }
.demo-fig .gi .gl { stroke-width: 1; opacity: .55; }
.demo-fig .gi.acc .gn { fill: var(--dm-acc); stroke: none; }
.demo-fig .gt { fill: var(--dm-t1); font-size: 15px; font-weight: 600; }
.demo-fig .gs { fill: var(--dm-t2); font-size: 12px; }
.demo-fig .gal { fill: var(--dm-t1); font-size: 12.5px; font-weight: 500; }
.demo-fig .gnote { fill: var(--dm-t2); font-size: 11.5px; font-style: italic; }
.demo-fig .gcap { fill: var(--dm-acc); font-size: 10px; font-weight: 700; letter-spacing: .14em; }
.demo-fig .gbr { fill: none; stroke: color-mix(in srgb, var(--dm-acc) 65%, transparent); stroke-width: 1.3; }
.demo-fig .ga { fill: none; stroke: color-mix(in srgb, var(--dm-t1) 72%, transparent); stroke-width: 1.6; stroke-linejoin: round; }
.demo-fig .gah { fill: color-mix(in srgb, var(--dm-t1) 72%, transparent); }
.demo .demo-foot a.demo-btn, .demo .demo-foot a.demo-btn:hover, .demo .demo-foot a.demo-btn:focus-visible { color: var(--dm-t1); text-decoration: none; display: inline-block; }
</style>

<div class="rintro" markdown="1">
AI is moving off the screen and into the world. Learned models are now being asked to
fly aircraft, drive vehicles, and manipulate objects &mdash; **physical AI**, where a
model's output is an action rather than a sentence. That changes what failure means: a
wrong action is executed, compounds through contact and dynamics, and cannot be taken
back. My research asks what it takes to build physical AI that can be trusted.

At the core is physical AI itself: learned dynamics models, controllers, and perception
systems that respect the physics they act in. Three pillars make that work trustworthy
&mdash; the **geometric foundations** that make guarantees tractable, **safe
reinforcement learning** for decisions under requirements that are never fully
specified, and **uncertainty quantification** so a system knows when it should not be
trusted. This agenda is supported by NSF, the FAA, NASA, the NSA, and Amazon.
</div>

<div class="tgrid">
<a class="tcard" href="#physical-ai">
<div class="ci"><i class="fas fa-robot" aria-hidden="true"></i></div>
<div class="cn">01</div>
<div class="ct">Physical AI</div>
<div class="cc">8 selected papers</div>
</a>
<a class="tcard" href="#geometry">
<div class="ci"><i class="fas fa-shapes" aria-hidden="true"></i></div>
<div class="cn">02</div>
<div class="ct">Geometric Foundations</div>
<div class="cc">9 selected papers</div>
</a>
<a class="tcard" href="#safe-rl">
<div class="ci"><i class="fas fa-shield-alt" aria-hidden="true"></i></div>
<div class="cn">03</div>
<div class="ct">Safe Reinforcement Learning</div>
<div class="cc">6 selected papers</div>
</a>
<a class="tcard" href="#uncertainty">
<div class="ci"><i class="fas fa-bullseye" aria-hidden="true"></i></div>
<div class="cn">04</div>
<div class="ct">Uncertainty Quantification</div>
<div class="cc">5 selected papers</div>
</a>
</div>

<div class="theme" id="physical-ai">
<div class="watermark" aria-hidden="true">01</div>
<div class="thead">
<div class="ticon"><i class="fas fa-robot" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Physical AI: Learning That Respects Physics</h2>
<div class="tsub">Dynamics, control, and perception for systems that act in the world</div>
</div>
</div>
<p class="tbody">A learned model of the physical world is only as trustworthy as the structure it
respects. A network fit to trajectory data will often predict well over a short horizon
while quietly violating the physics the real system obeys, and a controller that plans
on that model inherits every violation, compounded over the rollout. My work builds the
structure in rather than hoping it is learned: metriplectic flow matching that respects
the thermodynamics of dissipative systems, fast and accurate system identification, and
diagnostics for what neural PDE solvers actually learn. The same principle governs
control &mdash; Lyapunov&ndash;barrier networks that enforce stability and safety
jointly, model-predictive controllers that widen their safety margins when an ensemble
of learned models starts to disagree, and imitation learning that reweights corrupted
demonstrations so a robot does not inherit the mistakes in its data. New NSA-funded work
carries the principle into perception, developing tools to attack and certify the
symmetry-aware networks that encode 3D physical symmetries for LiDAR perception and
robotic manipulation.</p>
<div class="demo demo-drag" id="demo-phys">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Two learned models, one pendulum</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Animation of two learned models of the same pendulum, released from the same state. The unconstrained model gains energy with every swing until it goes over the top; the structure-preserving model loses energy, as a real pendulum does, and comes to rest."></canvas>
<div class="demo-foot"><span>Drag either bob to release both models from the same state.</span><button type="button" class="demo-btn" data-act="restart">Restart</button></div>
</div>
<ul class="papers">
<li><span class="pv">ECC</span><span class="pt">Metriplectic Conditional Flow Matching for Structure-Preserving Dynamics Learning</span><span class="py">2026</span></li>
<li><span class="pv">NeurIPS</span><span class="pt"><a href="https://arxiv.org/abs/2509.19526" target="_blank">Metriplectic Conditional Flow Matching for Dissipative Dynamics</a></span><span class="py">2025</span></li>
<li><span class="pv">PLOS ONE</span><span class="pt"><a href="https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0309661" target="_blank">Forward Variable Selection Enables Fast and Accurate Dynamic System Identification with Karhunen-Loève Decomposed Gaussian Processes</a></span><span class="py">2024</span></li>
<li><span class="pv">ICLR</span><span class="pt">What Does a Neural PDE Solver Really Learn? A Residual-Spectrum Diagnostic</span><span class="py">2026</span></li>
<li><span class="pv">RICO</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2666720725000426" target="_blank">Distributionally Robust Lyapunov-Barrier Networks for Safe and Stable Control Under Uncertainty</a></span><span class="py">2025</span></li>
<li><span class="pv">OJ-CSYS</span><span class="pt">How Much Do Your Models Disagree? Adaptive MPC Safety from Ensemble Uncertainty</span><span class="py">2026</span></li>
<li><span class="pv">ACC</span><span class="pt">Density-Ratio Weighted Behavioral Cloning: Learning Control Policies from Corrupted Datasets</span><span class="py">2026</span></li>
<li><span class="pv">EAAI</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/abs/pii/S0952197624010698" target="_blank">A Survey on Reinforcement Learning in Aviation Applications</a></span><span class="py">2024</span></li>
</ul>
</div>

<div class="theme" id="geometry">
<div class="watermark" aria-hidden="true">02</div>
<div class="thead">
<div class="ticon"><i class="fas fa-shapes" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Geometric Foundations for Trustworthy Learning</h2>
<div class="tsub">Optimal transport and the geometry of generative flows</div>
</div>
</div>
<p class="tbody">Every method here eventually asks how far apart two probability
distributions are. KL divergence is blind to the geometry of the underlying space,
treating beliefs on adjacent states as no closer than beliefs at opposite ends of it
&mdash; fatal for a safety argument, since <em>close</em> is the word every guarantee
turns on. Optimal transport measures how much probability mass must move and how far, so
error is expressed in the units of the state space: barycenters interpolate between
disagreeing agents, trust regions are bounded in transport cost, flows contract at
explicit rates. That last point is where the same geometry stops measuring and starts
generating. In its dynamic formulation a Wasserstein distance <em>is</em> a velocity
field carrying one distribution onto another &mdash; the object a flow matching model
learns. Constraining that field to be metriplectic, to remain on a manifold, or to
satisfy a temporal-logic specification is therefore not a second agenda but the same
one: shaping transport paths so a learned simulator is stable in the very metric its
guarantees are written in.</p>
<div class="demo demo-drag" id="demo-geo">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Blending optimism and pessimism with a Wasserstein barycenter</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Schematic animation of how WBSAC explores, shown at a single state with the actors held fixed. Each curve is a Gaussian policy over a one-dimensional action. The pessimistic actor maximizes the lower bound of the twin critics; the optimistic actor maximizes their mean plus a bonus for their disagreement, which pulls it toward actions the critics are unsure about. Actions are sampled from the Wasserstein barycenter of the two policies: a single Gaussian whose mean and standard deviation interpolate linearly, moving along the Wasserstein geodesic from the pessimistic actor to the optimistic one as the optimism weight grows from zero during training. For comparison, a KL-constrained exploration policy stays close to the pessimistic actor. Positions, widths and the KL radius are illustrative."></canvas>
<div class="demo-foot"><span>Drag the knob to change the blend. A KL constraint keeps exploration near the pessimistic actor; the barycenter can travel all the way. Schematic: one state, actors held fixed, illustrative sizes.</span><button type="button" class="demo-btn" data-act="toggle">Compare with a KL constraint</button></div>
</div>
<ul class="papers">
<li><span class="pv">L-CSS</span><span class="pt"><a href="https://ieeexplore.ieee.org/document/11563844" target="_blank">Blending Optimism and Pessimism via Wasserstein Barycenters for Continuous Control</a></span><span class="py">2026</span></li>
<li><span class="pv">CDC</span><span class="pt"><a href="https://arxiv.org/abs/2607.14291" target="_blank">Wasserstein Stability of Contracting Flows: Effective Rates, Euler Self-Correction, and Noise Tightening</a></span><span class="py">2026</span></li>
<li><span class="pv">L4DC</span><span class="pt">WAVE: Wasserstein Adaptive Value Estimation for Actor-Critic Reinforcement Learning</span><span class="py">2025</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2506.12497" target="_blank">Wasserstein-Barycenter Consensus for Cooperative Multi-Agent Reinforcement Learning</a></span><span class="py">2025</span></li>
<li><span class="pv">NeuS</span><span class="pt"><a href="https://arxiv.org/abs/2602.02009" target="_blank">Logic-Guided Vector Fields for Constrained Generative Modeling</a></span><span class="py">2026</span></li>
<li><span class="pv">ICLR</span><span class="pt">Geometry-Grounded Flow Matching on Compact Manifolds</span><span class="py">2026</span></li>
<li><span class="pv">NeurIPS</span><span class="pt">GeoReason: Step-Level Hallucination Detection via Hidden-State Trajectory Geometry</span><span class="py">2026</span></li>
<li><span class="pv">ACC</span><span class="pt"><a href="https://arxiv.org/abs/2509.14521" target="_blank">Geometry-Aware Decentralized Sinkhorn for Wasserstein Barycenters</a></span><span class="py">2026</span></li>
<li><span class="pv">NeurIPS</span><span class="pt">Understanding Reward Ambiguity Through Optimal Transport Theory in Inverse Reinforcement Learning</span><span class="py">2023</span></li>
</ul>
</div>

<div class="theme" id="safe-rl">
<div class="watermark" aria-hidden="true">03</div>
<div class="thead">
<div class="ticon"><i class="fas fa-shield-alt" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Safe and Constraint-Aware Reinforcement Learning</h2>
<div class="tsub">Policies that carry a safety argument, not just good average performance</div>
</div>
</div>
<p class="tbody">Most work on safe reinforcement learning assumes the constraint is handed
to you in closed form. For a robot or an aircraft it rarely is: the specification is
partial, expressed in temporal logic, implied by human corrections, or buried in a
dataset of demonstrations of unknown quality. My work learns the policy and the
constraint <em>together</em> &mdash; inferring unknown temporal specifications during
training, refining behavior from human feedback, and correcting offline policies for
constraints the data only implies. A recurring device is hierarchy: decomposing
long-horizon tasks so that safety can be reasoned about at the level of abstraction
where it is actually specified.</p>
<div class="demo demo-fig" id="demo-rl">
<div class="demo-head"><span class="demo-title"><span class="demo-tag">Method</span>Learning the safety rule and the policy together</span><span class="demo-hud demo-cite">IEEE OJ-CSYS 2024</span></div>
<div class="fig"><svg class="fw" viewBox="0 0 700 316" role="img" aria-label="Concept diagram. The safety rule and the policy are learned together. The rule starts with unknown parameters. The current rule constrains the policy; a human expert labels the policy’s behavior safe or unsafe; those labels refine the rule. The loop repeats until most rollouts are safe." xmlns="http://www.w3.org/2000/svg"><path class="gbr" d="M170,34 L170,22 L284,22 M416,22 L530,22 L530,34"/><text x="350" y="25.5" class="gcap" text-anchor="middle">LEARNED TOGETHER</text><rect class="gc acc" x="70" y="44" width="200" height="132" rx="14"/><g class="gi acc" transform="translate(170,74)"><path d="M0,-15 L12,-10 L12,0 C12,8 6.5,13 0,15.5 C-6.5,13 -12,8 -12,0 L-12,-10 Z"/><path d="M-5.5,0.5 L-1.5,4.5 L6,-4"/></g><text x="170" y="116" class="gt" text-anchor="middle">Safety rule</text><text x="170" y="136" class="gs" text-anchor="middle">parameters unknown,</text><text x="170" y="152" class="gs" text-anchor="middle">learned from labels</text><rect class="gc acc" x="430" y="44" width="200" height="132" rx="14"/><g class="gi acc" transform="translate(530,74)"><path class="gl" d="M-13,-7 L0,-12"/><path class="gl" d="M-13,-7 L0,0"/><path class="gl" d="M-13,-7 L0,12"/><path class="gl" d="M-13,7 L0,-12"/><path class="gl" d="M-13,7 L0,0"/><path class="gl" d="M-13,7 L0,12"/><path class="gl" d="M0,-12 L13,-6"/><path class="gl" d="M0,-12 L13,6"/><path class="gl" d="M0,0 L13,-6"/><path class="gl" d="M0,0 L13,6"/><path class="gl" d="M0,12 L13,-6"/><path class="gl" d="M0,12 L13,6"/><circle class="gn" cx="-13" cy="-7" r="3"/><circle class="gn" cx="-13" cy="7" r="3"/><circle class="gn" cx="0" cy="-12" r="3"/><circle class="gn" cx="0" cy="0" r="3"/><circle class="gn" cx="0" cy="12" r="3"/><circle class="gn" cx="13" cy="-6" r="3"/><circle class="gn" cx="13" cy="6" r="3"/></g><text x="530" y="116" class="gt" text-anchor="middle">Policy</text><text x="530" y="136" class="gs" text-anchor="middle">trained under</text><text x="530" y="152" class="gs" text-anchor="middle">the current rule</text><rect class="gc hum" x="245" y="232" width="210" height="70" rx="14"/><g class="gi hum" transform="translate(277,267)"><circle cx="0" cy="-7" r="5.5"/><path d="M-11,13 C-11,4 -6,0.5 0,0.5 C6,0.5 11,4 11,13"/></g><text x="305" y="255" class="gt" text-anchor="start">Human expert</text><text x="305" y="272" class="gs" text-anchor="start">labels behavior</text><text x="305" y="287" class="gs" text-anchor="start">safe or unsafe</text><polyline class="ga" points="270,96 422.5,96"/><polygon class="gah" points="430,96 422.5,99.9 422.5,92.1"/><text x="350" y="87" class="gal" text-anchor="middle">constrains</text><path class="ga" d="M530,176 C530,263 522.5,267 462.5,267"/><polygon class="gah" points="455,267 462.5,263.1 462.5,270.9"/><text x="542" y="220" class="gal" text-anchor="start">behavior</text><path class="ga" d="M245,267 C185,267 170,270.5 170,183.5"/><polygon class="gah" points="170,176 173.9,183.5 166.1,183.5"/><text x="158" y="220" class="gal" text-anchor="end">labels</text><text x="350" y="208" class="gnote" text-anchor="middle">repeat until most rollouts are safe</text></svg><svg class="ft2" viewBox="0 0 340 374" role="img" aria-label="Concept diagram. The safety rule and the policy are learned together. The rule starts with unknown parameters. The current rule constrains the policy; a human expert labels the policy’s behavior safe or unsafe; those labels refine the rule. The loop repeats until most rollouts are safe." xmlns="http://www.w3.org/2000/svg"><rect class="gc acc" x="34" y="10" width="290" height="78" rx="14"/><g class="gi acc" transform="translate(66,49)"><path d="M0,-15 L12,-10 L12,0 C12,8 6.5,13 0,15.5 C-6.5,13 -12,8 -12,0 L-12,-10 Z"/><path d="M-5.5,0.5 L-1.5,4.5 L6,-4"/></g><text x="94" y="37" class="gt" text-anchor="start">Safety rule</text><text x="94" y="54" class="gs" text-anchor="start">parameters unknown,</text><text x="94" y="69" class="gs" text-anchor="start">learned from labels</text><polyline class="ga" points="179,88 179,114.5"/><polygon class="gah" points="179,122 175.1,114.5 182.9,114.5"/><text x="189" y="109" class="gal" text-anchor="start">constrains</text><rect class="gc acc" x="34" y="122" width="290" height="78" rx="14"/><g class="gi acc" transform="translate(66,161)"><path class="gl" d="M-13,-7 L0,-12"/><path class="gl" d="M-13,-7 L0,0"/><path class="gl" d="M-13,-7 L0,12"/><path class="gl" d="M-13,7 L0,-12"/><path class="gl" d="M-13,7 L0,0"/><path class="gl" d="M-13,7 L0,12"/><path class="gl" d="M0,-12 L13,-6"/><path class="gl" d="M0,-12 L13,6"/><path class="gl" d="M0,0 L13,-6"/><path class="gl" d="M0,0 L13,6"/><path class="gl" d="M0,12 L13,-6"/><path class="gl" d="M0,12 L13,6"/><circle class="gn" cx="-13" cy="-7" r="3"/><circle class="gn" cx="-13" cy="7" r="3"/><circle class="gn" cx="0" cy="-12" r="3"/><circle class="gn" cx="0" cy="0" r="3"/><circle class="gn" cx="0" cy="12" r="3"/><circle class="gn" cx="13" cy="-6" r="3"/><circle class="gn" cx="13" cy="6" r="3"/></g><text x="94" y="149" class="gt" text-anchor="start">Policy</text><text x="94" y="166" class="gs" text-anchor="start">trained under</text><text x="94" y="181" class="gs" text-anchor="start">the current rule</text><polyline class="ga" points="179,200 179,226.5"/><polygon class="gah" points="179,234 175.1,226.5 182.9,226.5"/><text x="189" y="221" class="gal" text-anchor="start">behavior</text><rect class="gc hum" x="34" y="234" width="290" height="78" rx="14"/><g class="gi hum" transform="translate(66,273)"><circle cx="0" cy="-7" r="5.5"/><path d="M-11,13 C-11,4 -6,0.5 0,0.5 C6,0.5 11,4 11,13"/></g><text x="94" y="261" class="gt" text-anchor="start">Human expert</text><text x="94" y="278" class="gs" text-anchor="start">labels behavior</text><text x="94" y="293" class="gs" text-anchor="start">safe or unsafe</text><polyline class="ga" points="179,312 179,334 14,334 14,49 26.5,49"/><polygon class="gah" points="34,49 26.5,52.9 26.5,45.1"/><text x="102.5" y="327" class="gal" text-anchor="middle">labels</text><text x="170" y="360" class="gnote" text-anchor="middle">repeat until most rollouts are safe</text></svg></div>
<div class="demo-foot"><span>The rule’s parameters start unknown. The policy is trained under the current estimate of the rule, an expert labels its behavior safe or unsafe, and those labels refine the rule. The two are learned together until most rollouts are safe.</span><a class="demo-btn" href="https://ieeexplore.ieee.org/abstract/document/10569078" target="_blank" rel="noopener">Read the paper</a></div>
</div>
<ul class="papers">
<li><span class="pv">OJ-CSYS</span><span class="pt"><a href="https://ieeexplore.ieee.org/abstract/document/10569078" target="_blank">Concurrent Learning of Control Policy and Unknown Safety Specifications in Reinforcement Learning</a></span><span class="py">2024</span></li>
<li><span class="pv">ICAPS</span><span class="pt">Policy Refinement with Human Feedback for Safe Reinforcement Learning</span><span class="py">2023</span></li>
<li><span class="pv">RSS</span><span class="pt"><a href="https://arxiv.org/abs/2506.14058" target="_blank">Implicit Constraint-Aware Off-Policy Correction for Offline Reinforcement Learning</a></span><span class="py">2025</span></li>
<li><span class="pv">MDPI</span><span class="pt"><a href="https://www.mdpi.com/2227-7390/13/1/149" target="_blank">Multilevel Constrained Bandits: A Hierarchical Upper Confidence Bound Approach with Safety Guarantees</a></span><span class="py">2025</span></li>
<li><span class="pv">NeSy</span><span class="pt"><a href="https://openreview.net/forum?id=tXOU6EULup" target="_blank">Hierarchical Neuro-Symbolic Decision Transformer</a></span><span class="py">2025</span></li>
<li><span class="pv">RLC</span><span class="pt"><a href="https://arxiv.org/abs/2606.23933" target="_blank">Flow-Corrected Thompson Sampling for Non-Stationary Contextual Bandits</a></span><span class="py">2026</span></li>
</ul>
</div>

<div class="theme" id="uncertainty">
<div class="watermark" aria-hidden="true">04</div>
<div class="thead">
<div class="ticon"><i class="fas fa-bullseye" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Uncertainty Quantification and Calibrated Confidence</h2>
<div class="tsub">Systems that know when they should not be trusted</div>
</div>
</div>
<p class="tbody">Trustworthiness requires more than average accuracy: a deployed system needs
a defensible account of its own uncertainty, and a controller should become more
conservative exactly when its models are least reliable. Conformal prediction offers
distribution-free, finite-sample coverage guarantees, but standard formulations assume
flat, exchangeable data &mdash; an assumption a physical system breaks routinely as it
drifts into conditions its training data never covered. I extend it to settings with
real structure &mdash; hierarchical data with group-level effects, and predictions
living on manifolds &mdash; while preserving coverage, and study how conformal
ensembles hold up when the distribution shifts online. Applications run from
autonomous systems to clinical decision support.</p>
<div class="demo" id="demo-uq">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>A prediction interval that adapts</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Animation of a live data stream with a prediction line and a 90 percent prediction interval. When the data shifts and becomes noisier, points start falling outside the interval; the interval widens until coverage recovers, then narrows again when the shift ends."></canvas>
<div class="demo-foot"><span>Shift the data and watch the 90% interval miss, adapt, and recover.</span><button type="button" class="demo-btn" data-act="shift">Shift the data</button></div>
</div>
<ul class="papers">
<li><span class="pv">RAM</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2590037425000536" target="_blank">Conformal Prediction Across Scales: Finite-Sample Coverage with Hierarchical Efficiency</a></span><span class="py">2025</span></li>
<li><span class="pv">Sci. Rep.</span><span class="pt">A Hierarchical Conformal Framework for Uncertainty-Aware Length of Stay Prediction in Multi-Hospital Settings</span><span class="py">2026</span></li>
<li><span class="pv">AAAI</span><span class="pt"><a href="https://arxiv.org/abs/2601.01223" target="_blank">Adaptive Conformal Prediction via Bayesian Uncertainty Weighting for Hierarchical Healthcare Data</a></span><span class="py">2026</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2602.16015" target="_blank">Geometry-Aware Uncertainty Quantification via Conformal Prediction on Manifolds</a></span><span class="py">2026</span></li>
<li><span class="pv">Forecasting</span><span class="pt"><a href="https://www.mdpi.com/2571-9394/8/5/77" target="_blank">Heterogeneous-Horizon Conformal Ensembles for Online Prediction Under Distribution Shift: An Empirical Comparison with Strongly Adaptive Methods</a></span><span class="py">2026</span></li>
</ul>
</div>

<div class="rfund" markdown="1">

## Funding

<ul>
<li><span class="agency">Amazon</span> — Amazon Research Award (AWS Agentic AI): Trust-Aware Coordination for Multi-Agent LLM Systems on AWS, 2026<br><span class="role">PI</span></li>
<li><span class="agency">National Security Agency</span> — NCAE-C: Red-Teaming and Assurance for Geometric AI in Defense Autonomy, 2026&ndash;2028<br><span class="role">PI</span></li>
<li><span class="agency">National Science Foundation</span> — RII: Safety Validation of Autonomous Systems from Multiple Sources of Information, 2022&ndash;2024<br><span class="role">Single PI</span></li>
<li><span class="agency">Federal Aviation Administration</span> — Safety Verification Framework for Learning-based Aviation Systems (SVF-LAS), 2021&ndash;2023<br><span class="role">Lead PI</span></li>
<li><span class="agency">NASA</span> — Fault Diagnosis for Safety-Critical Autonomous Systems using Reinforcement Learning, 2021&ndash;2022<br><span class="role">Lead PI</span></li>
<li><span class="agency">National Science Foundation</span> — NRT-AI: AWARE-AI, AWAREness for Sensing Humans Responsibly with AI, 2021&ndash;2026<br><span class="role">Senior Personnel, co-lead of the software track</span></li>
</ul>

</div>

<p style="margin-top: 2.5rem; font-size: .9rem;">
A complete list of papers, filterable by theme, is on the
<a href="/publications/">publications page</a>.
</p>

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
   1. Physical AI: two learned models of one pendulum
   ================================================================ */
demo('demo-phys', function (d) {
var W2 = 6.8, OM = Math.sqrt(W2), TH0 = 1.1, TRAIL = 40, EMAX = 2.4;
var M = [{ z: -0.05, k: 1, key: 'warn', spr: 'sWarn', name: 'unconstrained model' },
{ z: 0.05, k: 1.012, key: 'acc', spr: 'sAcc', name: 'structure-preserving model' }];
var R = { z: 0.05, k: 1 };
var ALL = [M[0], M[1], R];
var th0 = TH0, t = 0, drag = -1, L = 70, py = 120, cx = [0, 0], e0 = 1, over = -1, burst = -1, narrow = false;
function setState(a) {
th0 = a; t = 0; over = -1; burst = -1;
ALL.forEach(function (m) { m.th = a; m.w = 0; m.tr = []; });
e0 = Math.max(1 - Math.cos(a), 0.02);
}
function energy(m) { return (1 - Math.cos(m.th)) + m.w * m.w / (2 * W2 * m.k); }
function pos(i, th) { return [cx[i] + L * Math.sin(th), py + L * Math.cos(th)]; }
function gx(i) { return cx[i] + L + Math.max(22, L * 0.34); }
function ey(e) { return py + L - Math.min(e, EMAX) * L; }
function sim(dt) {
var n = 6, h = dt / n, s, j, m;
for (s = 0; s < n; s++) {
for (j = 0; j < 3; j++) {
m = ALL[j];
m.w += h * (-W2 * m.k * Math.sin(m.th) - 2 * m.z * OM * m.w);
m.th += h * m.w;
}
}
t += dt;
ALL.forEach(function (mm) { mm.tr.push(mm.th); if (mm.tr.length > TRAIL) mm.tr.shift(); });
if (over < 0 && energy(M[0]) > 2) { over = t; burst = 0; }
if (burst >= 0) { burst += dt; if (burst > 1.2) burst = -1; }
}
function hud() {
d.setHud('<span class="dm-ring"></span>real pendulum &nbsp;&middot;&nbsp; t = <b>' + t.toFixed(1) + ' s</b>');
}
d.layout = function () {
narrow = d.W < 480;
L = Math.max(30, Math.min(d.W * 0.26 - 30, d.H * 0.27, 80));
py = 1.4 * L + 24;
cx = narrow ? [d.W * 0.23, d.W * 0.7] : [d.W * 0.24, d.W * 0.72];
};
d.step = function (dt) {
if (drag >= 0) return;
sim(dt);
if (t > 11 || (over >= 0 && t - over > 2.6)) setState(th0);
hud();
};
d.draw = function () {
var c = d.ctx, i, k;
d.clear();
for (i = 0; i < 2; i++) {
var m = M[i], color = P[m.key], b = pos(i, m.th), rb = pos(i, R.th), x = cx[i], g = gx(i), e = energy(m);
/* swing circle, the top of it, and the energy gauge aligned with it */
c.strokeStyle = col(P.hair); c.lineWidth = 1;
circle(c, x, py, L); c.stroke();
c.setLineDash([3, 4]); c.strokeStyle = col(P.mut, 0.55);
c.beginPath(); c.moveTo(x, py - L); c.lineTo(g + 9, py - L); c.stroke(); c.setLineDash([]);
rrect(c, g - 3, ey(EMAX), 6, ey(0) - ey(EMAX), 3); c.fillStyle = col(P.hair); c.fill();
var top = ey(e);
rrect(c, g - 3, top, 6, Math.max(6, ey(0) - top), 3); c.fillStyle = col(color); c.fill();
add(c, true); glow(c, P[m.spr], g, top + 2, 26, 0.7); add(c, false);
circle(c, g, ey(energy(R)), 4.2); c.strokeStyle = col(P.t1, 0.9); c.lineWidth = 1.5; c.stroke();
label(c, 'energy', g, ey(EMAX) - 7, { align: 'center', size: 10.5 });
/* real pendulum: a ghost ring on a faint rod */
c.strokeStyle = col(P.t1, 0.16); c.lineWidth = 1.5;
c.beginPath(); c.moveTo(x, py); c.lineTo(rb[0], rb[1]); c.stroke();
/* trail */
add(c, true); c.lineCap = 'round';
for (k = 1; k < m.tr.length; k++) {
var f = k / m.tr.length, p0 = pos(i, m.tr[k - 1]), p1 = pos(i, m.tr[k]);
c.strokeStyle = col(color, 0.05 + 0.5 * f * f); c.lineWidth = 1.5 + 3.5 * f;
c.beginPath(); c.moveTo(p0[0], p0[1]); c.lineTo(p1[0], p1[1]); c.stroke();
}
add(c, false);
/* rod, mount, bob */
c.strokeStyle = col(P.rod); c.lineWidth = 2;
c.beginPath(); c.moveTo(x, py); c.lineTo(b[0], b[1]); c.stroke();
c.beginPath(); c.moveTo(x - 9, py); c.lineTo(x + 9, py); c.stroke();
circle(c, x, py, 3); c.fillStyle = col(P.t1); c.fill();
add(c, true); glow(c, P[m.spr], b[0], b[1], 58, 0.95); add(c, false);
circle(c, b[0], b[1], 8.5); c.fillStyle = col(color); c.fill();
circle(c, b[0] - 2.4, b[1] - 2.6, 2.4); c.fillStyle = col(WHITE, 0.55); c.fill();
circle(c, rb[0], rb[1], 13.5); c.strokeStyle = col(P.t1, 0.75); c.lineWidth = 1.5; c.stroke();
/* names and status */
var ny = py + L + 26, fs = narrow ? 11.5 : 12.5, nm = narrow ? m.name.replace(' model', '') : m.name;
c.font = '500 ' + fs + 'px ' + FONT;
var nw = c.measureText(nm).width;
circle(c, x - nw / 2 - 9, ny - 4.5, 4.5); c.fillStyle = col(color); c.fill();
label(c, nm, x - nw / 2 + 1, ny, { size: fs, w: 500, color: P.t1 });
if (e > 2) {
warnMark(c, x - 41, ny + 19);
label(c, 'over the top', x - 31, ny + 19, { size: 11.5, w: 600, color: P.t1 });
} else {
var v = Math.round((e / e0 - 1) * 100);
label(c, 'energy ' + (v >= 0 ? '+' : '−') + Math.min(Math.abs(v), 999) + '%' + (narrow ? '' : ' since release'), x, ny + 19, { align: 'center', size: 11.5 });
}
if (i === 0 && burst >= 0) {
add(c, true);
c.strokeStyle = col(P.warn, 1 - burst / 1.2); c.lineWidth = 2;
circle(c, x, py - L, 8 + burst * 46); c.stroke();
add(c, false);
}
}
};
function project(a) { setState(a); for (var k = 0; k < 280; k++) sim(1 / 60); burst = -1; hud(); d.draw(); }
d.still = function () { project(TH0); };
d.act = function () { setState(TH0); hud(); };
function near(p) {
for (var i = 0; i < 2; i++) {
var b = pos(i, M[i].th), rb = pos(i, R.th);
if (Math.hypot(p[0] - b[0], p[1] - b[1]) < 30 || Math.hypot(p[0] - rb[0], p[1] - rb[1]) < 30) return i;
}
return -1;
}
function moveTo(p) { setState(clamp(Math.atan2(p[0] - cx[drag], p[1] - py), -2.7, 2.7)); hud(); }
d.cv.addEventListener('pointerdown', function (e) {
var p = d.pt(e), i = near(p);
if (i < 0) return;
drag = i; d.cv.setPointerCapture(e.pointerId); e.preventDefault();
d.cv.style.cursor = 'grabbing'; moveTo(p); if (!d.run) d.paint();
});
d.cv.addEventListener('pointermove', function (e) {
if (drag >= 0) { moveTo(d.pt(e)); if (!d.run) d.paint(); }
});
function up() { if (drag >= 0) { drag = -1; d.cv.style.cursor = ''; if (REDUCE) project(th0); } }
d.cv.addEventListener('pointerup', up);
d.cv.addEventListener('pointercancel', up);
setState(TH0); hud();
});
/* ================================================================
   2. Geometric foundations: blending optimism and pessimism with a
   Wasserstein barycenter (WBSAC, Shahrooei and Baheri, IEEE L-CSS 2026).
   The pessimistic actor maximizes the twin critics' lower bound (eq. 6); the
   optimistic actor maximizes their mean plus beta times their standard
   deviation (eq. 7). Actions are sampled from the W2 barycenter of the two
   Gaussian policies (eqs. 9-10: means and standard deviations interpolate
   linearly), which lies on the constant-speed W2 geodesic between them
   (Prop. 2). The optimism weight starts at zero and grows linearly during
   training (the schedule only increases; the loop restarts with a fade).
   Curves are true densities, so each encloses the same area. The comparison
   curve is drawn as in OAC: the pessimistic Gaussian with its mean shifted
   within a KL ball, which keeps exploration close to the pessimistic policy.
   Schematic of one state with the actors held fixed; positions, widths and
   the KL radius are illustrative.
   ================================================================ */
demo('demo-geo', function (d) {
var MP = -0.45, SP = 0.075, MO = 0.42, SO = 0.2, KLM = MP + SP * Math.SQRT2;
var xi = 0, phase = 0, pt = 0, fade = 0, drag = false, idle = 9, kl = false, time = 0, drops = [], acc = 0, geo = null, r = rng(9), ly2 = null, lyT = 0;
function hud() { d.setHud('optimism weight ξₒ <b>' + xi.toFixed(2) + '</b>'); }
d.heightFor = function (w) { return w < 540 ? 346 : 324; };
d.layout = function () {
var W = d.W, n = W < 540;
geo = { n: n, x0: n ? 18 : 40, x1: W - (n ? 18 : 40), top: 62 };
geo.base = geo.top + (n ? 162 : 152);
geo.ty = geo.base + (n ? 78 : 74); geo.tx0 = n ? 88 : Math.round(W * 0.27); geo.tx1 = W - geo.tx0;
ly2 = null;
};
function xa(a) { return geo.x0 + (a + 1) / 2 * (geo.x1 - geo.x0); }
/* a Gaussian density, scaled so that the pessimistic actor peaks at 1 */
function bell(a, mu, sg) { return Math.exp(-(a - mu) * (a - mu) / (2 * sg * sg)) * SP / sg; }
function yb(h) { return geo.base - h * (geo.base - geo.top); }
function path(c, fn) {
c.beginPath();
for (var k = 0; k <= 200; k++) { var a = -1 + k / 100, x = xa(a), y = yb(fn(a)); if (k) c.lineTo(x, y); else c.moveTo(x, y); }
}
function blend() { return [(1 - xi) * MP + xi * MO, (1 - xi) * SP + xi * SO]; }
/* screen y of the highest point of the pessimistic (and KL) curves between two x positions */
function tallest(xl, xr) {
var h = 0;
for (var x = xl; x <= xr; x += 1) { var a = (x - geo.x0) / (geo.x1 - geo.x0) * 2 - 1; h = Math.max(h, bell(a, MP, SP), kl ? bell(a, KLM, SP) : 0); }
return yb(h);
}
d.step = function (dt) {
time += dt; idle += dt;
/* autoplay: the weight rises from 0 to 1, pauses, then the run restarts behind a fade */
if (drag || idle <= 2.5) fade = 0;
else {
pt += dt;
if (phase === 0) { xi = Math.min(1, xi + dt / 7); if (xi >= 1) { phase = 1; pt = 0; } }
else if (phase === 1) { if (pt > 2.4) { phase = 2; pt = 0; } }
else if (phase === 2) { fade = Math.min(1, pt / 0.45); if (pt >= 0.45) { xi = 0; drops = []; ly2 = null; phase = 3; pt = 0; } }
else if (phase === 3) { fade = Math.max(0, 1 - pt / 0.45); if (pt >= 0.45) { fade = 0; phase = 4; pt = 0; } }
else if (pt > 0.6) { phase = 0; pt = 0; }
}
/* the agent tries actions drawn from the exploration policy */
acc += dt * 9;
var b = blend();
while (acc >= 1) { acc -= 1; drops.push({ a: clamp(b[0] + gauss(r) * b[1], -1, 1), t: 0 }); }
drops = drops.filter(function (q) { q.t += dt; return q.t < 1.1; });
hud();
};
d.draw = function () {
d.clear();
if (!geo) return;
var c = d.ctx, b = blend(), me = b[0], se = b[1], ph = geo.base - geo.top;
/* where the twin critics disagree (high epistemic uncertainty); the optimistic actor is pulled toward it */
var fx = xa(MO + 0.1), fy = geo.base - ph * 0.3, rx = (geo.x1 - geo.x0) * 0.28, ry = ph * 0.62, haze = 0.18;
c.save(); c.translate(fx, fy); c.scale(rx / ry, 1);
var g = c.createRadialGradient(0, 0, 0, 0, 0, ry);
g.addColorStop(0, col(P.t1, haze)); g.addColorStop(0.55, col(P.t1, haze * 0.7)); g.addColorStop(1, col(P.t1, 0));
c.fillStyle = g; circle(c, 0, 0, ry); c.fill(); c.restore();
if (geo.n) label(c, 'critics disagree here', geo.x1, geo.top + 6, { align: 'right', size: 11 });
else label(c, 'critics disagree here', fx, geo.base - ph * 0.86, { align: 'center', size: 11 });
c.fillStyle = col(P.hair); c.fillRect(geo.x0, geo.base, geo.x1 - geo.x0, 1);
label(c, 'action', geo.x1, geo.base + 20, { align: 'right', size: 11, a: 0.8 });
/* the two actors */
path(c, function (a) { return bell(a, MP, SP); }); c.lineTo(xa(1), geo.base); c.lineTo(xa(-1), geo.base); c.closePath();
c.fillStyle = col(P.mut, 0.2); c.fill();
path(c, function (a) { return bell(a, MP, SP); }); c.strokeStyle = col(P.mut); c.lineWidth = 1.8; c.stroke();
c.setLineDash([6, 4]); path(c, function (a) { return bell(a, MO, SO); }); c.strokeStyle = col(P.t1, 0.85); c.lineWidth = 1.6; c.stroke(); c.setLineDash([]);
if (kl) {
/* KL-constrained exploration: the pessimistic Gaussian, mean shifted within a KL ball (illustrative radius: 1 nat) */
c.setLineDash([2, 3]); path(c, function (a) { return bell(a, KLM, SP); });
c.strokeStyle = col(P.t1, 0.8); c.lineWidth = 2.2; c.stroke(); c.setLineDash([]);
}
/* the exploration policy: their Wasserstein barycenter, always one Gaussian */
path(c, function (a) { return bell(a, me, se); }); c.lineTo(xa(1), geo.base); c.lineTo(xa(-1), geo.base); c.closePath();
c.fillStyle = col(P.acc, P.dark ? 0.28 : 0.26); c.fill();
add(c, true); path(c, function (a) { return bell(a, me, se); }); c.strokeStyle = col(P.acc, 0.35); c.lineWidth = 8; c.stroke(); add(c, false);
path(c, function (a) { return bell(a, me, se); }); c.strokeStyle = col(P.acc); c.lineWidth = 2.4; c.stroke();
/* actions being tried */
add(c, true);
drops.forEach(function (q) {
var x = xa(q.a), top = yb(bell(q.a, me, se));
if (q.t < 0.4) glow(c, P.sAcc, x, top + (geo.base - top) * ease(q.t / 0.4), 10, 0.9);
else { c.fillStyle = col(P.acc, 0.8 * (1 - (q.t - 0.4) / 0.7)); c.fillRect(x - 0.75, geo.base - 7, 1.5, 7); }
});
add(c, false);
/* means slide along a straight line */
c.strokeStyle = col(P.t2, 0.7); c.lineWidth = 1.2; c.beginPath(); c.moveTo(xa(MP), geo.base + 0.5); c.lineTo(xa(MO), geo.base + 0.5); c.stroke();
circle(c, xa(MP), geo.base, 4); c.fillStyle = col(P.mut); c.fill();
circle(c, xa(MO), geo.base, 4); c.fillStyle = col(P.bg); c.fill(); c.strokeStyle = col(P.t1); c.lineWidth = 1.5; c.stroke();
var xm = xa(me);
c.beginPath(); c.moveTo(xm, geo.base - 6); c.lineTo(xm + 6, geo.base); c.lineTo(xm, geo.base + 6); c.lineTo(xm - 6, geo.base); c.closePath(); c.fillStyle = col(P.acc); c.fill();
/* labels */
label(c, geo.n ? 'pessimistic' : 'pessimistic actor', xa(MP), geo.base + 20, { align: 'center', size: 12, w: 500, color: P.t1 });
label(c, geo.n ? 'optimistic' : 'optimistic actor', xa(MO), geo.base + 20, { align: 'center', size: 12, w: 500, color: P.t1 });
label(c, geo.n ? 'critics’ lower bound' : 'maximizes the critics’ lower bound', xa(MP), geo.base + 35, { align: 'center', size: 11 });
label(c, geo.n ? 'mean + β·disagreement' : 'maximizes mean + β · disagreement', xa(MO), geo.base + 35, { align: 'center', size: 11 });
var pk = yb(bell(me, me, se)), lx = clamp(xm, geo.x0 + 80, geo.x1 - 80);
/* the label sits above the peak, rising just enough to clear the taller curves beneath it */
c.font = '600 12.5px ' + FONT; var hw1 = c.measureText('W₂ barycenter').width / 2 + 4;
c.font = '400 11px ' + FONT; var hw2 = c.measureText('the exploration policy').width / 2 + 4;
var target = Math.min(pk - 11, tallest(lx - hw2, lx + hw2) - 6, tallest(lx - hw1, lx + hw1) + 8), dtl = time - lyT;
/* rise at once (never overlap), settle back down gently */
lyT = time;
if (ly2 === null || !d.run || drag || dtl <= 0 || dtl > 0.2 || target < ly2) ly2 = target;
else ly2 += (target - ly2) * (1 - Math.exp(-dtl / 0.3));
var y2 = ly2;
/* a faint leader once the label has risen, unless a taller curve is in the way */
var la = 0.55 * clamp((pk - y2 - 20) / 8, 0, 1) * clamp((tallest(xm - 1, xm + 1) - pk + 2) / 10, 0, 1);
if (la > 0.01) { c.strokeStyle = col(P.t2, la); c.lineWidth = 1; c.beginPath(); c.moveTo(lx, y2 + 6); c.lineTo(xm, pk - 5); c.stroke(); }
label(c, 'W₂ barycenter', lx, y2 - 14, { align: 'center', size: 12.5, w: 600, color: P.t1 });
label(c, 'the exploration policy', lx, y2, { align: 'center', size: 11 });
if (kl) {
/* legend, in a strip above the curves that nothing else uses */
var ly = 19, room = geo.x1 - geo.x0 - 24, txt = 'KL-constrained exploration: stays near the pessimistic actor';
c.font = '400 11px ' + FONT;
if (c.measureText(txt).width > room) txt = 'KL-constrained: stays near the pessimistic actor';
if (c.measureText(txt).width > room) txt = 'KL-constrained exploration';
c.setLineDash([2, 3]); c.strokeStyle = col(P.t1, 0.8); c.lineWidth = 2.2;
c.beginPath(); c.moveTo(geo.x0, ly - 4); c.lineTo(geo.x0 + 18, ly - 4); c.stroke(); c.setLineDash([]);
label(c, txt, geo.x0 + 24, ly, { size: 11 });
}
/* the optimism weight */
var tx0 = geo.tx0, tx1 = geo.tx1, ty = geo.ty, kx = tx0 + xi * (tx1 - tx0);
label(c, 'pessimistic', tx0 - 18, ty + 4, { align: 'right', size: 11 });
label(c, 'optimistic', tx1 + 18, ty + 4, { size: 11 });
rrect(c, tx0, ty - 3, tx1 - tx0, 6, 3); c.fillStyle = col(P.hair); c.fill();
rrect(c, tx0, ty - 3, Math.max(6, kx - tx0), 6, 3); c.fillStyle = col(P.acc); c.fill();
add(c, true); glow(c, P.sAcc, kx, ty, 30, 0.7); add(c, false);
circle(c, kx, ty, 7.5); c.fillStyle = col(P.bg); c.fill(); c.strokeStyle = col(P.acc); c.lineWidth = 2.5; c.stroke();
label(c, 'optimism weight ξₒ starts at 0 and grows linearly during training', (tx0 + tx1) / 2, ty + 22, { align: 'center', size: 11 });
if (fade > 0) { c.globalAlpha = fade; c.drawImage(d.bgc, 0, 0, d.W, d.H); c.globalAlpha = 1; }
};
d.still = function () { xi = 0.5; fade = 0; drops = []; ly2 = null; hud(); d.draw(); };
d.act = function (a, btn) { kl = !kl; btn.textContent = kl ? 'Hide the KL constraint' : 'Compare with a KL constraint'; };
function onTrack(p) { return geo && Math.abs(p[1] - geo.ty) < 18 && p[0] > geo.tx0 - 16 && p[0] < geo.tx1 + 16; }
function seek(p) { xi = clamp((p[0] - geo.tx0) / (geo.tx1 - geo.tx0), 0, 1); phase = xi >= 1 ? 1 : 0; pt = 0; fade = 0; idle = 0; hud(); }
d.cv.addEventListener('pointerdown', function (e) {
var p = d.pt(e);
if (!onTrack(p)) return;
drag = true; d.cv.setPointerCapture(e.pointerId); e.preventDefault(); seek(p);
if (!d.run) d.paint();
});
d.cv.addEventListener('pointermove', function (e) {
var p = d.pt(e);
if (drag) { seek(p); if (!d.run) d.paint(); }
else d.cv.style.cursor = onTrack(p) ? 'ew-resize' : '';
});
function up() { if (drag) { drag = false; idle = 0; } }
d.cv.addEventListener('pointerup', up);
d.cv.addEventListener('pointercancel', up);
hud();
});
/* ================================================================
   4. Uncertainty: a live prediction interval through a shift
   ================================================================ */
demo('demo-uq', function (d) {
var r = rng(5), NW = 70, TICK = 0.16, acc = 0, n = 0, pts = [], R = [], alpha = 0.1;
var shift = false, left = 0, spans = [], auto = 5, touched = false, VN = NW, btn = d.el.querySelector('[data-act="shift"]');
d.layout = function () { VN = d.W < 480 ? 46 : NW; };
for (var i = 0; i < 40; i++) R.push(Math.abs(gauss(r) * 0.08));
function mean(k) { return 0.5 * Math.sin(k / 7) + 0.22 * Math.sin(k / 2.9 + 1); }
function quant(arr, lev) {
if (lev >= 1) return Math.max.apply(null, arr);
var s = arr.slice().sort(function (x, y) { return x - y; });
return s[clamp(Math.ceil(lev * s.length) - 1, 0, s.length - 1)];
}
function setShift(on) {
shift = on; left = on ? 70 : 0;
if (on) spans.push({ a: n, b: -1 });
else if (spans.length && spans[spans.length - 1].b < 0) spans[spans.length - 1].b = n;
if (btn) btn.textContent = on ? 'End the shift' : 'Shift the data';
}
function tick() {
var m = mean(n), q = quant(R.slice(-40), 1 - alpha), y = m + gauss(r) * (shift ? 0.27 : 0.08), miss = Math.abs(y - m) > q;
pts.push({ n: n, m: m, y: y, q: q, miss: miss, age: 0 });
if (pts.length > NW + 2) pts.shift();
R.push(Math.abs(y - m)); if (R.length > 120) R.shift();
/* adaptive conformal inference: widen after a miss, narrow slowly after a hit */
alpha = clamp(alpha + 0.05 * (0.1 - (miss ? 1 : 0)), 0, 0.5);
spans = spans.filter(function (s) { return s.b < 0 || s.b > n - NW - 2; });
n++;
if (shift && --left <= 0) setShift(false);
}
function hud() {
var w = pts.slice(-20), cov = w.length ? Math.round(100 * w.filter(function (p) { return !p.miss; }).length / w.length) : 100;
d.setHud('coverage, last 20 points <b>' + cov + '%</b> &nbsp;&middot;&nbsp; target 90%');
}
for (i = 0; i < 160; i++) tick();
pts.forEach(function (p) { p.age = 1; });
function X(k) { return d.W - 26 - (n - 1 - k + acc / TICK) * ((d.W - 34) / (VN - 1)); }
function Y(v) { return d.H * 0.47 - v * d.H * 0.29; }
d.step = function (dt) {
acc += dt;
while (acc >= TICK) { acc -= TICK; tick(); }
pts.forEach(function (p) { p.age += dt; });
if (!touched && !shift) { auto -= dt; if (auto <= 0) { setShift(true); auto = 14; } }
hud();
};
d.draw = function () {
var c = d.ctx, k, p, x, y, s;
d.clear();
c.save(); c.beginPath(); c.rect(0, 0, d.W, d.H - 24); c.clip();
/* shaded shift periods */
spans.forEach(function (sp) {
var x0 = Math.max(0, X(sp.a - 0.5)), x1 = sp.b < 0 ? d.W : X(sp.b - 0.5);
if (x1 <= 0) return;
c.fillStyle = col(P.warn, 0.09); c.fillRect(x0, 0, x1 - x0, d.H);
c.fillStyle = col(P.warn, 0.7); c.fillRect(x0, 0, 1, d.H);
var sl = sp.b < 0 ? 'data shifted' : 'shift';
c.font = '400 11.5px ' + FONT;
if (x0 + 14 + c.measureText(sl).width < d.W) label(c, sl, x0 + 7, 18, { size: 11.5, color: P.t1 });
else label(c, sl, x0 - 7, 18, { size: 11.5, color: P.t1, align: 'right' });
});
/* 90% interval */
c.beginPath();
pts.forEach(function (q, j) { var xx = X(q.n), yy = Y(q.m + q.q); if (j) c.lineTo(xx, yy); else c.moveTo(xx, yy); });
for (k = pts.length - 1; k >= 0; k--) c.lineTo(X(pts[k].n), Y(pts[k].m - pts[k].q));
c.closePath(); c.fillStyle = col(P.acc, P.dark ? 0.22 : 0.24); c.fill();
c.strokeStyle = col(P.acc, 0.5); c.lineWidth = 1; c.stroke();
/* prediction, with a soft glow */
c.beginPath();
pts.forEach(function (q, j) { var xx = X(q.n), yy = Y(q.m); if (j) c.lineTo(xx, yy); else c.moveTo(xx, yy); });
c.lineJoin = 'round';
add(c, true); c.strokeStyle = col(P.acc, 0.22); c.lineWidth = 7; c.stroke(); add(c, false);
c.strokeStyle = col(P.acc); c.lineWidth = 2; c.stroke();
/* observations */
add(c, true);
for (k = 0; k < pts.length; k++) {
p = pts[k]; x = X(p.n); y = Y(p.y); s = Math.min(1, p.age / 0.18 + 0.2);
if (p.miss) {
glow(c, P.sWarn, x, y, 26 * s, 0.75);
if (p.age < 0.8) { c.strokeStyle = col(P.warn, 1 - p.age / 0.8); c.lineWidth = 2; circle(c, x, y, 5 + p.age * 30); c.stroke(); }
} else glow(c, P.sMut, x, y, 12 * s, 0.45);
}
add(c, false);
for (k = 0; k < pts.length; k++) {
p = pts[k]; x = X(p.n); y = Y(p.y); s = Math.min(1, p.age / 0.18 + 0.2);
if (p.miss) {
circle(c, x, y, 6.5 * s); c.fillStyle = col(P.bg); c.fill();
c.strokeStyle = col(P.warn); c.lineWidth = 2; circle(c, x, y, 4.5 * s); c.stroke();
} else { circle(c, x, y, 2.8 * s); c.fillStyle = col(P.mut); c.fill(); }
}
c.restore();
/* legend */
var ly = d.H - 9;
circle(c, 18, ly - 4, 2.8); c.fillStyle = col(P.mut); c.fill();
var w1 = label(c, 'covered', 26, ly, { size: 11 });
c.strokeStyle = col(P.warn); c.lineWidth = 2; circle(c, 44 + w1, ly - 4, 4); c.stroke();
var w2 = label(c, 'missed', 53 + w1, ly, { size: 11 });
c.fillStyle = col(P.acc, 0.35); c.fillRect(71 + w1 + w2, ly - 9, 18, 10);
c.fillStyle = col(P.acc); c.fillRect(71 + w1 + w2, ly - 4.5, 18, 2);
label(c, '90% prediction interval', 95 + w1 + w2, ly, { size: 11 });
};
d.still = function () { d.draw(); };
d.act = function () { touched = true; setShift(!shift); };
(function preset() {
if (!REDUCE) return;
pts = []; spans = []; n = 0;
for (var j = 0; j < NW; j++) { if (j === 30) setShift(true); tick(); }
if (shift) setShift(false);
pts.forEach(function (p) { p.age = 1; });
})();
hud();
});
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
