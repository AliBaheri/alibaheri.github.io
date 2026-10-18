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
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Two beliefs, one consensus</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Animation of two clouds of points, the beliefs of two agents. Optimal transport moves each point along a straight line until the clouds merge into one shared belief halfway between them, the Wasserstein barycenter. The pointwise average instead keeps two separate clouds with nothing in between."></canvas>
<div class="demo-foot"><span>Drag either belief. Transport merges them into one; averaging keeps two.</span><button type="button" class="demo-btn" data-act="toggle">Show the average</button></div>
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
<div class="demo" id="demo-rl">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Learning where not to go</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Animation of an agent travelling from start to goal over five episodes. A hidden unsafe region lies on the direct route. In early episodes the agent cuts through it and each violation is counted; a learned constraint grows around the region, and later episodes route around it with no violations."></canvas>
<div class="demo-foot"><span>The agent learns the constraint from its own mistakes, then stops making them.</span><button type="button" class="demo-btn" data-act="replay">Replay</button></div>
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
   2. Geometric foundations: two beliefs, one consensus
   ================================================================ */
demo('demo-geo', function (d) {
var N = 170, r = rng(11), Z = [], ph = [], i;
for (i = 0; i < N; i++) { Z.push([clamp(gauss(r), -2.5, 2.5), clamp(gauss(r), -2.5, 2.5)]); ph.push(r() * 6.283); }
var A = { fx: 0.2, fy: 0.47, sx: 0.05, sy: 0.115 }, B = { fx: 0.8, fy: 0.53, sx: 0.125, sy: 0.065 };
var t = 0, T = 10, mode = 'bary', drag = null, time = 0, wave = -1, sc = 200;
d.layout = function () { sc = Math.min(d.H, d.W * 0.6); };
function blend(tt) {
if (tt < 1.2) return 0;
if (tt < 3.8) return ease((tt - 1.2) / 2.6);
if (tt < 7.0) return 1;
if (tt < 8.6) return 1 - ease((tt - 7.0) / 1.6);
return 0;
}
function pt(o, k) { return [o.fx * d.W + o.sx * sc * Z[k][0], o.fy * d.H + o.sy * sc * Z[k][1]]; }
function hud() {
d.setHud('combining by <b>' + (mode === 'bary' ? 'Wasserstein barycenter' : 'pointwise average') + '</b>');
}
d.step = function (dt) {
time += dt;
var t0 = t;
t = (t + dt) % T;
if (mode === 'bary' && t0 < 3.8 && t >= 3.8) wave = 0;
if (wave >= 0) { wave += dt; if (wave > 1.3) wave = -1; }
};
d.draw = function (forceE) {
var c = d.ctx, e = forceE != null ? forceE : (REDUCE ? 1 : blend(t)), k, wob, pa, pb, qa, qb;
var ca = [A.fx * d.W, A.fy * d.H], cb = [B.fx * d.W, B.fy * d.H], m = [(ca[0] + cb[0]) / 2, (ca[1] + cb[1]) / 2];
var sbar = (A.sy + B.sy) / 2 * sc;
d.clear();
add(c, true);
if (mode === 'bary') {
if (e > 0.01) {
for (k = 0; k < N; k++) { pa = pt(A, k); pb = pt(B, k); glow(c, P.sMut, pa[0], pa[1], 7, 0.22 * e); glow(c, P.sMut, pb[0], pb[1], 7, 0.22 * e); }
var th = 0.2 * Math.sin(Math.PI * e);
if (th > 0.01) {
c.strokeStyle = col(P.acc, th); c.lineWidth = 1;
c.beginPath();
for (k = 0; k < N; k += 2) {
pa = pt(A, k); pb = pt(B, k);
var mid = [(pa[0] + pb[0]) / 2, (pa[1] + pb[1]) / 2];
c.moveTo(pa[0], pa[1]); c.lineTo(pa[0] + (mid[0] - pa[0]) * e, pa[1] + (mid[1] - pa[1]) * e);
c.moveTo(pb[0], pb[1]); c.lineTo(pb[0] + (mid[0] - pb[0]) * e, pb[1] + (mid[1] - pb[1]) * e);
}
c.stroke();
}
}
for (k = 0; k < N; k++) {
wob = 0.9 * Math.sin(time * 1.6 + ph[k]);
pa = pt(A, k); pb = pt(B, k);
var pm = [(pa[0] + pb[0]) / 2, (pa[1] + pb[1]) / 2];
qa = [pa[0] + (pm[0] - pa[0]) * e + wob, pa[1] + (pm[1] - pa[1]) * e - wob];
qb = [pb[0] + (pm[0] - pb[0]) * e - wob, pb[1] + (pm[1] - pb[1]) * e + wob];
if (e < 0.99) { glow(c, P.sMut, qa[0], qa[1], 13, 0.55 * (1 - e)); glow(c, P.sMut, qb[0], qb[1], 13, 0.55 * (1 - e)); }
if (e > 0.01) { glow(c, P.sAcc, qa[0], qa[1], 14, 0.6 * e); glow(c, P.sAcc, qb[0], qb[1], 14, 0.6 * e); }
}
if (wave >= 0) {
c.strokeStyle = col(P.acc, 0.7 * (1 - wave / 1.3)); c.lineWidth = 2;
circle(c, m[0], m[1], sbar * 1.2 + wave * 90); c.stroke();
}
add(c, false);
if (e > 0.6) label(c, 'barycenter: one shared belief', m[0], Math.min(m[1] + sbar * 2.4 + 20, d.H - 10), { align: 'center', size: 12.5, w: 500, color: P.t1, a: Math.min(1, (e - 0.6) * 4) });
} else {
var dim = 1 - 0.5 * e;
for (k = 0; k < N; k++) {
wob = 0.9 * Math.sin(time * 1.6 + ph[k]);
pa = pt(A, k); pb = pt(B, k);
glow(c, P.sMut, pa[0] + wob, pa[1] - wob, 13, 0.55 * dim);
glow(c, P.sMut, pb[0] - wob, pb[1] + wob, 13, 0.55 * dim);
}
add(c, false);
if (e > 0.5) {
var ra = sbar * 1.5, al = Math.min(1, (e - 0.5) * 4);
c.globalAlpha = al; c.setLineDash([5, 5]); c.strokeStyle = col(P.warn); c.lineWidth = 2;
circle(c, m[0], m[1], ra); c.stroke(); c.setLineDash([]); c.globalAlpha = 1;
c.font = '500 12.5px ' + FONT;
var s = 'the average puts nothing here', w = c.measureText(s).width, ly = Math.min(m[1] + ra + 24, d.H - 10);
warnMark(c, m[0] - w / 2 - 4, ly, al);
label(c, s, m[0] - w / 2 + 6, ly, { size: 12.5, w: 500, color: P.t1, a: al });
}
}
add(c, false);
if (e < 0.4 || mode !== 'bary') {
var la = mode === 'bary' ? 1 - e / 0.4 : 1;
label(c, "agent 1's belief", ca[0], Math.min(ca[1] + A.sy * sc * 2.5 + 18, d.H - 10), { align: 'center', a: la });
label(c, "agent 2's belief", cb[0], Math.min(cb[1] + B.sy * sc * 2.5 + 18, d.H - 10), { align: 'center', a: la });
}
};
d.still = function () { d.draw(1); };
d.act = function (a, btn) {
mode = mode === 'bary' ? 'avg' : 'bary';
btn.textContent = mode === 'bary' ? 'Show the average' : 'Show the barycenter';
t = 0.9; wave = -1; hud();
};
function which(p) {
var a = [A.fx * d.W, A.fy * d.H], b = [B.fx * d.W, B.fy * d.H];
if (Math.hypot(p[0] - a[0], p[1] - a[1]) < Math.max(44, 2.4 * A.sy * sc)) return A;
if (Math.hypot(p[0] - b[0], p[1] - b[1]) < Math.max(44, 2.4 * B.sx * sc)) return B;
return null;
}
d.cv.addEventListener('pointerdown', function (e) {
var o = which(d.pt(e));
if (!o) return;
drag = o; d.cv.setPointerCapture(e.pointerId); e.preventDefault(); d.cv.style.cursor = 'grabbing';
});
d.cv.addEventListener('pointermove', function (e) {
if (!drag) return;
var p = d.pt(e);
drag.fx = clamp(p[0] / d.W, 0.1, 0.9); drag.fy = clamp(p[1] / d.H, 0.25, 0.72);
if (!d.run) d.paint();
});
function up() { if (drag) { drag = null; d.cv.style.cursor = ''; } }
d.cv.addEventListener('pointerup', up);
d.cv.addEventListener('pointercancel', up);
hud();
});
/* ================================================================
   3. Safe RL: learning where not to go
   ================================================================ */
demo('demo-rl', function (d) {
var EP = 5, DUR = 2.5, GAP = 0.9, ENDHOLD = 3;
/* path bend per episode; clearance from the true region (in region radii) is
   0.10, 0.75 (both inside: violations), then 1.51, 1.31, 1.21 (outside) */
var DEV = [0, 0.45, 1.0, 0.85, 0.78], EST = [0.6, 1.12, 1.12, 1.12, 1.12];
var S, G, Zn, ep, t, vio, epHit, est, estTo, traces, trail, rip, phase, wait, flash, pops, reach;
function restart() {
ep = 0; t = 0; vio = 0; epHit = false; est = 0; estTo = 0; traces = []; trail = []; rip = []; pops = [];
phase = 'run'; wait = 0; flash = 0; reach = -1; hud();
}
d.layout = function () {
S = [d.W * 0.08, d.H * 0.7]; G = [d.W * 0.92, d.H * 0.38];
Zn = { x: d.W * 0.5, y: d.H * 0.56, rx: Math.min(d.W * 0.14, 110), ry: d.H * 0.2 };
};
function bez(e, u) {
var dy = DEV[e] * d.H * 0.4, v = 1 - u;
var c1 = [S[0] + (G[0] - S[0]) * 0.3, S[1] + (G[1] - S[1]) * 0.3 - dy];
var c2 = [S[0] + (G[0] - S[0]) * 0.7, S[1] + (G[1] - S[1]) * 0.7 - dy];
return [v * v * v * S[0] + 3 * v * v * u * c1[0] + 3 * v * u * u * c2[0] + u * u * u * G[0],
v * v * v * S[1] + 3 * v * v * u * c1[1] + 3 * v * u * u * c2[1] + u * u * u * G[1]];
}
function inside(p) { var x = (p[0] - Zn.x) / Zn.rx, y = (p[1] - Zn.y) / Zn.ry; return x * x + y * y < 1; }
function hud() { d.setHud('episode <b>' + Math.min(ep + 1, EP) + '</b>/' + EP + ' &nbsp;&middot;&nbsp; violations <b>' + vio + '</b>'); }
function finish() { traces.push({ e: ep, bad: epHit }); estTo = EST[ep]; reach = 0; }
d.step = function (dt) {
est += (estTo - est) * Math.min(1, dt * 3.5);
rip = rip.filter(function (q) { q.a += dt; return q.a < 0.9; });
pops = pops.filter(function (q) { q.a += dt; return q.a < 1.6; });
if (reach >= 0) { reach += dt; if (reach > 0.9) reach = -1; }
flash = Math.max(0, flash - dt * 1.6);
if (phase === 'run') {
var prev = bez(ep, ease(Math.min(t / DUR, 1)));
t += dt;
var p = bez(ep, ease(Math.min(t / DUR, 1)));
if (inside(p)) {
flash = 1;
if (!inside(prev)) { rip.push({ x: p[0], y: p[1], a: 0 }); pops.push({ x: p[0], y: p[1], a: 0 }); if (!epHit) { epHit = true; vio++; } }
}
trail.push(p); if (trail.length > 36) trail.shift();
if (t >= DUR) { finish(); phase = 'gap'; wait = 0; }
hud();
} else {
wait += dt;
if (phase === 'gap' && wait > GAP) {
if (ep + 1 >= EP) { phase = 'end'; wait = 0; } else { ep++; t = 0; epHit = false; trail = []; phase = 'run'; hud(); }
} else if (phase === 'end' && wait > ENDHOLD) restart();
}
};
d.draw = function () {
var c = d.ctx, k, q;
d.clear();
/* the true unsafe region: hatched, unknown to the agent; flashes on contact */
c.save();
c.beginPath(); c.ellipse(Zn.x, Zn.y, Zn.rx, Zn.ry, 0, 0, 2 * Math.PI); c.clip();
c.fillStyle = col(P.warn, 0.05 + 0.2 * flash); c.fillRect(Zn.x - Zn.rx, Zn.y - Zn.ry, 2 * Zn.rx, 2 * Zn.ry);
c.strokeStyle = col(P.mut, 0.2); c.lineWidth = 1; c.beginPath();
for (k = -2 * Zn.ry; k < 2 * Zn.rx + 2 * Zn.ry; k += 9) { c.moveTo(Zn.x - Zn.rx + k, Zn.y - Zn.ry); c.lineTo(Zn.x - Zn.rx + k - 2 * Zn.ry, Zn.y + Zn.ry); }
c.stroke(); c.restore();
c.setLineDash([4, 4]); c.strokeStyle = col(P.mut, 0.6); c.lineWidth = 1;
c.beginPath(); c.ellipse(Zn.x, Zn.y, Zn.rx, Zn.ry, 0, 0, 2 * Math.PI); c.stroke(); c.setLineDash([]);
label(c, 'unsafe region (hidden from the agent)', Zn.x, Zn.y + Zn.ry * 1.12 + 21, { align: 'center', size: 11.5 });
/* learned constraint */
if (est > 0.03) {
add(c, true);
c.strokeStyle = col(P.acc, 0.16); c.lineWidth = 7;
c.beginPath(); c.ellipse(Zn.x, Zn.y, Zn.rx * est, Zn.ry * est, 0, 0, 2 * Math.PI); c.stroke();
add(c, false);
c.setLineDash([7, 5]); c.strokeStyle = col(P.acc); c.lineWidth = 2;
c.beginPath(); c.ellipse(Zn.x, Zn.y, Zn.rx * est, Zn.ry * est, 0, 0, 2 * Math.PI); c.stroke(); c.setLineDash([]);
if (est > 0.3) label(c, 'learned constraint', Zn.x + Zn.rx * est + 10, Zn.y + 4, { size: 11.5, w: 500, color: P.t1, a: Math.min(1, (est - 0.3) * 4) });
}
/* finished episodes */
c.lineWidth = 1.6;
traces.forEach(function (tr) {
c.strokeStyle = col(tr.bad ? P.warn : P.acc, 0.6);
c.beginPath(); c.moveTo(S[0], S[1]);
for (var j = 1; j <= 70; j++) { var q = bez(tr.e, j / 70); c.lineTo(q[0], q[1]); }
c.stroke();
});
/* the agent's comet trail */
add(c, true); c.lineCap = 'round';
for (k = 1; k < trail.length; k++) {
var f = k / trail.length;
c.strokeStyle = col(P.acc, 0.05 + 0.6 * f * f); c.lineWidth = 1.5 + 4 * f;
c.beginPath(); c.moveTo(trail[k - 1][0], trail[k - 1][1]); c.lineTo(trail[k][0], trail[k][1]); c.stroke();
}
rip.forEach(function (q) { c.strokeStyle = col(P.warn, 1 - q.a / 0.9); c.lineWidth = 2; circle(c, q.x, q.y, 6 + q.a * 48); c.stroke(); });
add(c, false);
/* start and goal */
circle(c, S[0], S[1], 7); c.strokeStyle = col(P.t1); c.lineWidth = 2; c.stroke();
label(c, 'start', S[0], S[1] + 23, { align: 'center' });
add(c, true); glow(c, P.sAcc, G[0], G[1], 34, 0.6);
if (reach >= 0) { c.strokeStyle = col(P.acc, 1 - reach / 0.9); c.lineWidth = 2; circle(c, G[0], G[1], 8 + reach * 34); c.stroke(); }
add(c, false);
circle(c, G[0], G[1], 9); c.strokeStyle = col(P.t1); c.lineWidth = 1.5; c.stroke();
circle(c, G[0], G[1], 4); c.fillStyle = col(P.t1); c.fill();
label(c, 'goal', G[0], G[1] + 25, { align: 'center' });
/* the agent */
if (phase === 'run') {
var p = bez(ep, ease(Math.min(t / DUR, 1))), bad = inside(p);
add(c, true); glow(c, bad ? P.sWarn : P.sAcc, p[0], p[1], 52, 1); add(c, false);
circle(c, p[0], p[1], 7); c.fillStyle = col(bad ? P.warn : P.acc); c.fill();
circle(c, p[0] - 2, p[1] - 2.2, 2); c.fillStyle = col(WHITE, 0.6); c.fill();
}
pops.forEach(function (q) {
var a = q.a < 1.1 ? 1 : 1 - (q.a - 1.1) / 0.5, y = q.y - 20 - q.a * 10;
warnMark(c, q.x - 30, y, a);
label(c, 'violation', q.x - 20, y, { size: 11.5, w: 600, color: P.t1, a: a });
});
/* legend and verdict */
var ly = d.H - 12;
c.lineWidth = 2;
c.strokeStyle = col(P.warn, 0.8); c.beginPath(); c.moveTo(14, ly - 4); c.lineTo(30, ly - 4); c.stroke();
var w1 = label(c, 'violating episode', 36, ly, { size: 11 });
c.strokeStyle = col(P.acc); c.beginPath(); c.moveTo(52 + w1, ly - 4); c.lineTo(68 + w1, ly - 4); c.stroke();
label(c, 'safe episode', 74 + w1, ly, { size: 11 });
if (phase === 'end') label(c, 'episodes 3–5: zero violations', d.W / 2, 24, { align: 'center', size: 13, w: 600, color: P.t1, a: Math.min(1, wait * 2.5) });
};
d.still = function () {
restart();
for (var e = 0; e < EP; e++) {
var hit = false;
for (var k = 0; k <= 70; k++) if (inside(bez(e, k / 70))) hit = true;
traces.push({ e: e, bad: hit }); if (hit) vio++;
}
ep = EP - 1; est = estTo = EST[EP - 1]; phase = 'end'; wait = 1; hud(); d.draw();
};
d.act = function () { restart(); };
restart();
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
