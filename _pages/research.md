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
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Blending optimism and pessimism with a Wasserstein barycenter</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Animation of how WBSAC explores. A pessimistic actor, a narrow bell, plays it safe on a known good action. An optimistic actor, a wide bell, bets on actions the critics are unsure about. The exploration policy is their Wasserstein barycenter: a single bell whose center and width move smoothly from the pessimistic actor to the optimistic one as the optimism weight rises during training. A plain mixture would instead split into two separate humps."></canvas>
<div class="demo-foot"><span>Drag the knob to change the blend. The barycenter stays one policy; a mixture splits in two.</span><button type="button" class="demo-btn" data-act="toggle">Show the mixture</button></div>
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
<div class="demo demo-drag" id="demo-rl">
<div class="demo-head"><span class="demo-title"><span class="demo-live"><i></i>Live</span>Learning the safety rule and the policy together</span><span class="demo-hud" data-hud></span></div>
<canvas role="img" aria-label="Animation of our method for learning an unknown safety specification during training. A robot circles an arena whose true safety limits, two vertical lines, are hidden from it. The specification is a parametric signal temporal logic formula, always stay between theta 1 and theta 2, with unknown limits. Each iteration, Bayesian optimization fits the limits to runs that an expert labeled safe or unsafe, the policy is retrained under the new limits, and the expert labels new runs. The learned limits converge to the true ones and the runs become safe."></canvas>
<div class="demo-foot"><span>Drag an amber line to hide a new rule; the robot learns it from scratch.</span><button type="button" class="demo-btn" data-act="replay">Restart</button></div>
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
   Wasserstein barycenter (WBSAC, abstract view). A pessimistic actor plays
   it safe; an optimistic actor bets on actions the critics are unsure about.
   The exploration policy is their W2 barycenter: one Gaussian whose mean and
   width blend linearly with the optimism weight, which rises during training.
   ================================================================ */
demo('demo-geo', function (d) {
var MP = -0.45, SP = 0.075, MO = 0.42, SO = 0.2, SREF = 0.075;
var xi = 0, dir = 1, hold = 0, drag = false, idle = 9, mix = false, time = 0, drops = [], acc = 0, geo = null, r = rng(9);
function hud() { d.setHud('optimism weight ξ <b>' + xi.toFixed(2) + '</b>'); }
d.heightFor = function (w) { return w < 540 ? 300 : 280; };
d.layout = function () {
var W = d.W, n = W < 540;
geo = { n: n, x0: n ? 18 : 40, x1: W - (n ? 18 : 40), top: 34, base: n ? 196 : 186 };
geo.ty = geo.base + (n ? 62 : 58); geo.tx0 = n ? 88 : Math.round(W * 0.27); geo.tx1 = W - geo.tx0;
};
function xa(a) { return geo.x0 + (a + 1) / 2 * (geo.x1 - geo.x0); }
function bell(a, mu, sg) { return Math.exp(-(a - mu) * (a - mu) / (2 * sg * sg)) * Math.min(1, Math.sqrt(SREF / sg)); }
function yb(h) { return geo.base - h * (geo.base - geo.top); }
function path(c, fn) {
c.beginPath();
for (var k = 0; k <= 160; k++) { var a = -1 + k / 80, x = xa(a), y = yb(fn(a)); if (k) c.lineTo(x, y); else c.moveTo(x, y); }
}
function blend() { return [(1 - xi) * MP + xi * MO, (1 - xi) * SP + xi * SO]; }
d.step = function (dt) {
time += dt; idle += dt;
if (!drag && idle > 2.5) {
if (hold > 0) { hold -= dt; if (hold <= 0) dir = xi >= 1 ? -1 : 1; }
else if (dir < 0) { xi = Math.max(0, xi - dt / 1.2); if (xi <= 0) { dir = 1; hold = 0.8; } }
else { xi = Math.min(1, xi + dt / 7); if (xi >= 1) hold = 2.4; }
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
var c = d.ctx, b = blend(), me = b[0], se = b[1];
/* actions the critics are unsure about: a soft haze that thins as they get explored */
var fx = xa(MO), fy = geo.base - (geo.base - geo.top) * 0.42, rx = (geo.x1 - geo.x0) * 0.3, ry = (geo.base - geo.top) * 0.72, haze = 0.2 * (1 - 0.6 * xi);
c.save(); c.translate(fx, fy); c.scale(rx / ry, 1);
var g = c.createRadialGradient(0, 0, 0, 0, 0, ry);
g.addColorStop(0, col(P.t1, haze)); g.addColorStop(0.55, col(P.t1, haze * 0.7)); g.addColorStop(1, col(P.t1, 0));
c.fillStyle = g; circle(c, 0, 0, ry); c.fill(); c.restore();
label(c, 'critics disagree here', fx + rx * 0.55, geo.top + 4, { align: 'center', size: 11 });
c.fillStyle = col(P.hair); c.fillRect(geo.x0, geo.base, geo.x1 - geo.x0, 1);
/* the two actors */
path(c, function (a) { return bell(a, MP, SP); }); c.lineTo(xa(1), geo.base); c.lineTo(xa(-1), geo.base); c.closePath();
c.fillStyle = col(P.mut, 0.2); c.fill();
path(c, function (a) { return bell(a, MP, SP); }); c.strokeStyle = col(P.mut); c.lineWidth = 1.8; c.stroke();
c.setLineDash([6, 4]); path(c, function (a) { return bell(a, MO, SO); }); c.strokeStyle = col(P.t1, 0.85); c.lineWidth = 1.6; c.stroke(); c.setLineDash([]);
if (mix) {
c.setLineDash([2, 3]); path(c, function (a) { return (1 - xi) * bell(a, MP, SP) + xi * bell(a, MO, SO); });
c.strokeStyle = col(P.t1, 0.75); c.lineWidth = 2.2; c.stroke(); c.setLineDash([]);
}
/* the exploration policy: their Wasserstein barycenter, always one bell */
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
var pk = yb(bell(me, me, se)), lx = clamp(xm, geo.x0 + 80, geo.x1 - 80);
label(c, 'W₂ barycenter', lx, pk - 22, { align: 'center', size: 12.5, w: 600, color: P.t1 });
label(c, 'the exploration policy', lx, pk - 8, { align: 'center', size: 11 });
if (mix) {
c.setLineDash([2, 3]); c.strokeStyle = col(P.t1, 0.75); c.lineWidth = 2.2;
c.beginPath(); c.moveTo(geo.x0, geo.top + 2); c.lineTo(geo.x0 + 18, geo.top + 2); c.stroke(); c.setLineDash([]);
label(c, 'plain mixture', geo.x0 + 24, geo.top + 6, { size: 11 });
}
/* the optimism weight */
var tx0 = geo.tx0, tx1 = geo.tx1, ty = geo.ty, kx = tx0 + xi * (tx1 - tx0);
label(c, 'pessimistic', tx0 - 12, ty + 4, { align: 'right', size: 11 });
label(c, 'optimistic', tx1 + 12, ty + 4, { size: 11 });
rrect(c, tx0, ty - 3, tx1 - tx0, 6, 3); c.fillStyle = col(P.hair); c.fill();
rrect(c, tx0, ty - 3, Math.max(6, kx - tx0), 6, 3); c.fillStyle = col(P.acc); c.fill();
add(c, true); glow(c, P.sAcc, kx, ty, 30, 0.7); add(c, false);
circle(c, kx, ty, 7.5); c.fillStyle = col(P.bg); c.fill(); c.strokeStyle = col(P.acc); c.lineWidth = 2.5; c.stroke();
label(c, 'optimism weight ξ rises as training goes on', (tx0 + tx1) / 2, ty + 22, { align: 'center', size: 11 });
};
d.still = function () { xi = 0.5; drops = []; hud(); d.draw(); };
d.act = function (a, btn) { mix = !mix; btn.textContent = mix ? 'Hide the mixture' : 'Show the mixture'; };
function onTrack(p) { return geo && Math.abs(p[1] - geo.ty) < 18 && p[0] > geo.tx0 - 16 && p[0] < geo.tx1 + 16; }
function seek(p) { xi = clamp((p[0] - geo.tx0) / (geo.tx1 - geo.tx0), 0, 1); hold = 0; idle = 0; hud(); }
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
   3. Safe RL: learning an unknown safety rule and the policy together
   (illustration of concurrent policy / pSTL-parameter learning on the
   Circle task: Bayesian optimization fits the rule's limits to runs an
   expert labels, the policy is retrained under each estimate, and the
   loop stops once 90% of a round's runs are safe)
   ================================================================ */
demo('demo-rl', function (d) {
var RC = 1.5, M = 0.08, SD = 0.035, KS = 25, BONUS = 0.008, NROLL = 10, TR = 0.14, NG = 30, MAXIT = 9;
var B1 = [-1.6, -0.4], B2 = [0.4, 1.6], PAPER = [-1.2, 1.0], SEED = 1;
var r = rng(7), time = 0, geo = null, dragging = -1, hoverLine = -1, userRule = false;
var truth, data, prev, warm, bo, ppath, it, phase, pt, est, shownLim, limFrom, limT, pol, polFrom, polTo, polT;
var shownTr, oldTr, revealed, roundSafe, conv, heat, heatOld, heatT, phi = 0, trail = [];
var STEPS = ['fit the rule (Bayesian opt.)', 'retrain the policy (RL)', 'expert labels new runs'];
var STEPS_S = ['fit rule', 'retrain policy', 'label runs'];
function U(a, b) { return a + (b - a) * r(); }
function toT(u) { return [B1[0] + u[0] * (B1[1] - B1[0]), B2[0] + u[1] * (B2[1] - B2[0])]; }
function toU(t) { return [(t[0] - B1[0]) / (B1[1] - B1[0]), (t[1] - B2[0]) / (B2[1] - B2[0])]; }
function run(lo, hi, safe) { return { lo: Math.max(lo, -RC), hi: Math.min(hi, RC), safe: safe, w: r() * 6.283 }; }
function initialData() {
var out = [], k;
for (k = 0; k < 10; k++) out.push(run(truth[0] + U(0.12, 0.35), truth[1] - U(0.12, 0.35), true));
for (k = 0; k < 10; k++) {
if (k % 2) out.push(run(truth[0] - U(0.7, 1.0), truth[1] - U(0.12, 0.35), false));
else out.push(run(truth[0] + U(0.12, 0.35), truth[1] + U(0.7, 1.0), false));
}
return out;
}
/* objective: misclassification of the labeled runs by the rule (smoothed), with a
   slight preference for the least restrictive rule among equally good ones */
function sig(z) { return 1 / (1 + Math.exp(-Math.max(-40, Math.min(40, z)))); }
function obj(t1, t2) {
var es = 0, eu = 0, ns = 0, nu = 0, i, q, rho;
for (i = 0; i < data.length; i++) {
q = data[i]; rho = Math.min(q.lo - t1, t2 - q.hi);
if (q.safe) { es += sig(-KS * rho); ns++; } else { eu += sig(KS * rho); nu++; }
}
return 0.5 * (es / Math.max(ns, 1) + eu / Math.max(nu, 1)) - BONUS * (t2 - t1) / 2.8;
}
/* a small Gaussian-process surrogate with expected improvement */
function kern(a, b) { var x = a[0] - b[0], y = a[1] - b[1]; return Math.exp(-(x * x + y * y) / (2 * 0.12 * 0.12)); }
function chol(A, n) {
var L = [], i, j, k, s;
for (i = 0; i < n; i++) L.push(new Float64Array(n));
for (i = 0; i < n; i++) for (j = 0; j <= i; j++) {
s = A[i][j];
for (k = 0; k < j; k++) s -= L[i][k] * L[j][k];
L[i][j] = i === j ? Math.sqrt(Math.max(s, 1e-12)) : s / L[j][j];
}
return L;
}
function fsub(L, b, n) { var x = new Float64Array(n), i, k, s; for (i = 0; i < n; i++) { s = b[i]; for (k = 0; k < i; k++) s -= L[i][k] * x[k]; x[i] = s / L[i][i]; } return x; }
function bsub(L, y, n) { var x = new Float64Array(n), i, k, s; for (i = n - 1; i >= 0; i--) { s = y[i]; for (k = i + 1; k < n; k++) s -= L[k][i] * x[k]; x[i] = s / L[i][i]; } return x; }
function erf(x) {
var sg = x < 0 ? -1 : 1, t;
x = Math.abs(x); t = 1 / (1 + 0.3275911 * x);
return sg * (1 - ((((1.061405429 * t - 1.453152027) * t + 1.421413741) * t - 0.284496736) * t + 0.254829592) * t * Math.exp(-x * x));
}
function nextEI(Us, F, C) {
var n = Us.length, i, j, mu0 = 0, best = Infinity, K = [], bi = 0, bv = -1;
for (i = 0; i < n; i++) { mu0 += F[i] / n; best = Math.min(best, F[i]); }
for (i = 0; i < n; i++) { K.push(new Float64Array(n)); for (j = 0; j < n; j++) K[i][j] = kern(Us[i], Us[j]) + (i === j ? 1e-3 : 0); }
var L = chol(K, n), y = new Float64Array(n);
for (i = 0; i < n; i++) y[i] = F[i] - mu0;
var a = bsub(L, fsub(L, y, n), n), ks = new Float64Array(n);
for (var c = 0; c < C.length; c++) {
for (i = 0; i < n; i++) ks[i] = kern(C[c], Us[i]);
var mu = mu0, v = fsub(L, ks, n), vv = 0;
for (i = 0; i < n; i++) { mu += ks[i] * a[i]; vv += v[i] * v[i]; }
var sd = Math.sqrt(Math.max(1e-12, 1 - vv)), g = best - mu - 0.005, z = g / sd;
var ei = g * 0.5 * (1 + erf(z / Math.SQRT2)) + sd * Math.exp(-0.5 * z * z) / 2.5066;
if (ei > bv) { bv = ei; bi = c; }
}
return C[bi];
}
function runBO() {
var Us = [], F = [], k, lo, hi, C = [], gi, gj;
function ev(u) { u = [clamp(u[0], 0, 1), clamp(u[1], 0, 1)]; var t = toT(u); Us.push(u); F.push(obj(t[0], t[1])); }
warm.forEach(ev);
if (prev) { ev(prev); [[0.03, 0], [0, 0.03], [-0.03, 0], [0, -0.03]].forEach(function (q) { ev([prev[0] + q[0], prev[1] + q[1]]); }); }
lo = prev ? [clamp(prev[0] - TR, 0, 1), clamp(prev[1] - TR, 0, 1)] : [0, 0];
hi = prev ? [clamp(prev[0] + TR, 0, 1), clamp(prev[1] + TR, 0, 1)] : [1, 1];
for (gi = 0; gi < NG; gi++) for (gj = 0; gj < NG; gj++) C.push([lo[0] + (hi[0] - lo[0]) * gi / (NG - 1), lo[1] + (hi[1] - lo[1]) * gj / (NG - 1)]);
for (k = 0; k < 3; k++) ev([lo[0] + r() * (hi[0] - lo[0]), lo[1] + r() * (hi[1] - lo[1])]);
for (k = 0; k < 10; k++) { var c = nextEI(Us, F, C); ev([c[0] + gauss(r) * 0.003, c[1] + gauss(r) * 0.003]); }
var bf = Math.min.apply(null, F), bi = 0, bw = -1;
for (k = 0; k < F.length; k++) if (F[k] <= bf + 1e-12) { var t = toT(Us[k]); if (t[1] - t[0] > bw) { bw = t[1] - t[0]; bi = k; } }
var idx = F.map(function (f, kk) { return kk; }).sort(function (p, q) { return F[p] - F[q]; });
warm = idx.slice(0, 3).map(function (kk) { return Us[kk]; });
prev = Us[bi];
return { U: Us, F: F, best: bi };
}
function nominal(t) { return t ? [Math.max(t[0] + M, -RC), Math.min(t[1] - M, RC)] : [-RC, RC]; }
function rollout(t) {
var n = nominal(t), lo = n[0] > -RC ? n[0] + gauss(r) * SD : -RC, hi = n[1] < RC ? n[1] + gauss(r) * SD : RC;
lo = Math.max(lo, -RC); hi = Math.min(hi, RC);
return { lo: lo, hi: hi, safe: lo >= truth[0] && hi <= truth[1], w: r() * 6.283 };
}
function makeHeat() {
var c = document.createElement('canvas'), n = 40, g, i, j, v;
c.width = c.height = n; g = c.getContext('2d');
for (i = 0; i < n; i++) for (j = 0; j < n; j++) {
var t = toT([(i + 0.5) / n, 1 - (j + 0.5) / n]);
v = Math.pow(clamp(1 - (obj(t[0], t[1]) + 0.01) / 0.36, 0, 1), 2.2);
g.fillStyle = col(P.acc, 0.03 + 0.72 * v); g.fillRect(i, j, 1, 1);
}
c.acc = P.acc.join();
return c;
}
function hud() { d.setHud('iteration <b>' + it + '</b> &middot; labeled runs <b>' + data.length + '</b>'); }
function counts() { var s = 0; data.forEach(function (q) { if (q.safe) s++; }); return [s, data.length - s]; }
/* the loop: compute steps (shared by the animation and the still frame) */
function doFit() { it++; heatOld = heat; heat = makeHeat(); heatT = 0; bo = runBO(); est = toT(bo.U[bo.best]); ppath.push(bo.U[bo.best]); }
function doLabel() { var tr = [], k; for (k = 0; k < NROLL; k++) tr.push(rollout(est)); roundSafe = tr.filter(function (q) { return q.safe; }).length; return tr; }
function newRun(randomRule, seed) {
r = rng(seed != null ? seed : (Math.random() * 1e9) | 0);
if (randomRule) { truth = [-U(0.85, 1.35), U(0.75, 1.3)]; }
data = initialData(); prev = null; warm = []; ppath = []; it = 0; est = null; shownLim = null; limFrom = null; limT = 1;
pol = nominal(null); polFrom = pol; polTo = pol; polT = 1;
shownTr = data.slice(); oldTr = []; revealed = shownTr.length; roundSafe = -1; conv = false; bo = null;
heatOld = null; heat = makeHeat(); heatT = 1; phase = 'intro'; pt = 0; hud();
}
function startFit() { doFit(); oldTr = shownTr; shownTr = []; revealed = 0; phase = 'fit'; pt = 0; hud(); }
function startTrain() {
oldTr = [];
limFrom = shownLim ? shownLim.slice() : null; shownLim = est.slice(); limT = 0;
polFrom = pol.slice(); polTo = nominal(est); polT = 0; phase = 'train'; pt = 0;
}
function startLabel() { oldTr = []; shownTr = doLabel(); revealed = 0; phase = 'label'; pt = 0; }
function endRound() {
data = data.concat(shownTr); hud();
if (roundSafe >= 9 || it >= MAXIT) { conv = roundSafe >= 9; phase = 'done'; pt = 0; } else startFit();
}
d.heightFor = function (w) { return w < 560 ? 622 : 360; };
d.layout = function () {
var W = d.W, H = d.H, w, x0, s;
if (W >= 560) {
w = Math.round(W * 0.49); x0 = 12 + w + 18; s = 136;
geo = { narrow: false, pills: 20, world: { x: 12, y: 40, w: w, h: H - 70 }, fx: x0, fy: 60, map: { x: x0 + 20, y: 130, s: s } };
geo.stats = geo.map.x + s + 16; geo.sum = H - 13;
} else {
s = 140;
geo = { narrow: true, pills: 18, world: { x: 10, y: 34, w: W - 20, h: 250 }, fx: 16, fy: 348, map: { x: 34, y: 416, s: s } };
geo.stats = geo.map.x + s + 16; geo.sum = H - 13;
}
var wd = geo.world;
geo.sc = Math.min(wd.w / 3.9, wd.h / 3.7); geo.cx = wd.x + wd.w / 2; geo.cy = wd.y + wd.h / 2 + 4;
};
function wx(x) { return geo.cx + x * geo.sc; }
function wy(y) { return geo.cy - y * geo.sc; }
function mx(u) { return geo.map.x + u * geo.map.s; }
function my(u) { return geo.map.y + (1 - u) * geo.map.s; }
d.step = function (dt) {
time += dt; heatT = Math.min(1, heatT + dt * 2); limT = Math.min(1, limT + dt / 0.7);
if (phase === 'train') polT = Math.min(1, pt / 1.0);
pol = [polFrom[0] + (polTo[0] - polFrom[0]) * ease(polT), polFrom[1] + (polTo[1] - polFrom[1]) * ease(polT)];
phi += dt * 1.7;
var x = clamp(RC * Math.cos(phi), pol[0], pol[1]), y = RC * Math.sin(phi);
trail.push([x, y]); if (trail.length > 28) trail.shift();
if (dragging >= 0) return;
pt += dt;
if (phase === 'intro') { if (pt > 1.8) startFit(); }
else if (phase === 'fit') { if (pt > 0.25 + bo.U.length * 0.065 + 0.4) startTrain(); }
else if (phase === 'train') { if (pt > 1.35) startLabel(); }
else if (phase === 'label') { revealed = Math.min(NROLL, Math.floor(pt / 0.13) + 1); if (pt > NROLL * 0.13 + 0.5) endRound(); }
else if (phase === 'done') { if (pt > 7) newRun(!userRule); }
};
function tracePath(c, q) {
c.beginPath();
for (var k = 0; k <= 64; k++) {
var a = k / 64 * 6.2832, rr = RC * (1 + 0.012 * Math.sin(3 * a + q.w));
var x = clamp(rr * Math.cos(a), q.lo, q.hi), y = rr * Math.sin(a);
if (k) c.lineTo(wx(x), wy(y)); else c.moveTo(wx(x), wy(y));
}
}
function drawWorld(c) {
var wd = geo.world, k, x, i;
/* regions outside the true limits: unsafe, hidden from the robot */
[[wd.x, wx(truth[0])], [wx(truth[1]), wd.x + wd.w]].forEach(function (z) {
c.save(); rrect(c, wd.x, wd.y, wd.w, wd.h, 10); c.clip();
c.beginPath(); c.rect(z[0], wd.y, z[1] - z[0], wd.h); c.clip();
c.fillStyle = col(P.warn, 0.07); c.fillRect(z[0], wd.y, z[1] - z[0], wd.h);
c.strokeStyle = col(P.warn, 0.14); c.lineWidth = 1; c.beginPath();
for (k = z[0] - wd.h; k < z[1]; k += 9) { c.moveTo(k, wd.y + wd.h); c.lineTo(k + wd.h, wd.y); }
c.stroke(); c.restore();
});
for (i = 0; i < 2; i++) {
x = wx(truth[i]);
c.setLineDash([5, 4]); c.strokeStyle = col(P.warn, hoverLine === i || dragging === i ? 1 : 0.75); c.lineWidth = hoverLine === i || dragging === i ? 2.5 : 1.5;
c.beginPath(); c.moveTo(x, wd.y + 6); c.lineTo(x, wd.y + wd.h - 6); c.stroke(); c.setLineDash([]);
if (dragging === i || hoverLine === i) label(c, 'true limit ' + truth[i].toFixed(2), i ? x - 6 : x + 6, wd.y + 34, { align: i ? 'right' : 'left', size: 11.5, w: 500, color: P.t1 });
}
/* the circle the robot is rewarded for following */
c.strokeStyle = col(P.hair); c.lineWidth = 1; circle(c, geo.cx, geo.cy, RC * geo.sc); c.stroke();
/* the learned rule: a band between the estimated limits */
if (shownLim) {
var e = ease(limT), L0 = limFrom ? limFrom[0] + (shownLim[0] - limFrom[0]) * e : shownLim[0], L1 = limFrom ? limFrom[1] + (shownLim[1] - limFrom[1]) * e : shownLim[1];
var a0 = Math.max(wx(L0), wd.x), a1 = Math.min(wx(L1), wd.x + wd.w);
c.fillStyle = col(P.acc, 0.07); c.fillRect(a0, wd.y, a1 - a0, wd.h);
[L0, L1].forEach(function (v, j) {
var xx = wx(v);
if (xx < wd.x || xx > wd.x + wd.w) return;
add(c, true); c.strokeStyle = col(P.acc, 0.18); c.lineWidth = 7; c.beginPath(); c.moveTo(xx, wd.y + 6); c.lineTo(xx, wd.y + wd.h - 6); c.stroke(); add(c, false);
c.strokeStyle = col(P.acc); c.lineWidth = 2; c.beginPath(); c.moveTo(xx, wd.y + 6); c.lineTo(xx, wd.y + wd.h - 6); c.stroke();
label(c, (j ? 'θ₂ = ' : 'θ₁ = ') + v.toFixed(2), clamp(xx, wd.x + 34, wd.x + wd.w - 34), wd.y + wd.h - 10, { align: 'center', size: 11.5, w: 500, color: P.t1 });
});
}
/* runs: last round (fading) and the current one, colored by the expert's label */
var drawSet = function (set, n, alpha) {
for (k = 0; k < Math.min(n, set.length); k++) {
var q = set[k];
tracePath(c, q); c.strokeStyle = col(q.safe ? P.acc : P.warn, (q.safe ? 0.42 : 0.8) * alpha); c.lineWidth = q.safe ? 1.1 : 1.4; c.stroke();
if (!q.safe && alpha > 0.5) {
var vx = q.lo < truth[0] ? q.lo : q.hi;
circle(c, wx(vx), wy(0), 3); c.fillStyle = col(P.warn, alpha); c.fill();
}
}
};
var fade = phase === 'fit' ? Math.max(0, 1 - pt / 0.8) : 1;
if (oldTr.length && phase === 'fit') drawSet(oldTr, oldTr.length, fade);
drawSet(shownTr, phase === 'label' ? revealed : shownTr.length, phase === 'intro' || phase === 'label' || phase === 'done' ? 1 : fade);
/* the robot following its current policy */
var cur = trail[trail.length - 1] || [RC, 0], bad = cur[0] < truth[0] || cur[0] > truth[1];
add(c, true); c.lineCap = 'round';
for (k = 1; k < trail.length; k++) {
var f = k / trail.length;
c.strokeStyle = col(P.acc, 0.05 + 0.5 * f * f); c.lineWidth = 1.5 + 3 * f;
c.beginPath(); c.moveTo(wx(trail[k - 1][0]), wy(trail[k - 1][1])); c.lineTo(wx(trail[k][0]), wy(trail[k][1])); c.stroke();
}
glow(c, bad ? P.sWarn : P.sAcc, wx(cur[0]), wy(cur[1]), 44, 1);
add(c, false);
circle(c, wx(cur[0]), wy(cur[1]), 6.5); c.fillStyle = col(bad ? P.warn : P.acc); c.fill();
circle(c, wx(cur[0]) - 1.8, wy(cur[1]) - 2, 1.8); c.fillStyle = col(WHITE, 0.6); c.fill();
label(c, 'Circle task, top view', wd.x + 10, wd.y + 17, { size: 11 });
c.strokeStyle = col(P.hair); c.lineWidth = 1; rrect(c, wd.x + 0.5, wd.y + 0.5, wd.w - 1, wd.h - 1, 10); c.stroke();
/* legend under the panel */
var ly = wd.y + wd.h + 16, lx = wd.x + 2, wl;
c.strokeStyle = col(P.acc, 0.85); c.lineWidth = 1.6; c.beginPath(); c.moveTo(lx, ly - 4); c.lineTo(lx + 14, ly - 4); c.stroke();
wl = label(c, 'safe run', lx + 19, ly, { size: 11 }); lx += 19 + wl + 14;
c.strokeStyle = col(P.warn, 0.85); c.beginPath(); c.moveTo(lx, ly - 4); c.lineTo(lx + 14, ly - 4); c.stroke();
wl = label(c, 'unsafe run', lx + 19, ly, { size: 11 }); lx += 19 + wl + 14;
c.setLineDash([3, 3]); c.strokeStyle = col(P.warn, 0.85); c.beginPath(); c.moveTo(lx + 4, ly - 10); c.lineTo(lx + 4, ly + 2); c.stroke(); c.setLineDash([]);
wl = label(c, 'true limit (hidden, drag me)', lx + 12, ly, { size: 11 });
}
function drawPills(c) {
var labels = geo.narrow ? STEPS_S : STEPS, fs = geo.narrow ? 11 : 11.5, ws = [], tot = 0, gap = geo.narrow ? 16 : 22, k, act = phase === 'fit' ? 0 : phase === 'train' ? 1 : phase === 'label' ? 2 : -1;
c.font = '500 ' + fs + 'px ' + FONT;
for (k = 0; k < 3; k++) { ws.push(c.measureText((k + 1) + '  ' + labels[k]).width + 20); tot += ws[k]; }
tot += gap * 2;
var x = Math.round((d.W - tot) / 2), y = geo.pills - 10;
for (k = 0; k < 3; k++) {
var on = k === act;
rrect(c, x, y, ws[k], 20, 10);
c.fillStyle = col(P.acc, on ? 0.24 : 0.05); c.fill();
c.strokeStyle = col(on ? P.acc : P.hair, on ? 0.9 : 1); c.lineWidth = 1; c.stroke();
if (on) { add(c, true); glow(c, P.sAcc, x + 11, y + 10, 26, 0.5); add(c, false); }
label(c, (k + 1) + '  ' + labels[k], x + 10, y + 14, { size: fs, w: 500, color: on ? P.t1 : P.t2 });
x += ws[k];
if (k < 2) {
c.strokeStyle = col(P.t2, 0.7); c.lineWidth = 1.2; c.beginPath();
c.moveTo(x + 4, y + 10); c.lineTo(x + gap - 5, y + 10); c.moveTo(x + gap - 9, y + 6.5); c.lineTo(x + gap - 5, y + 10); c.lineTo(x + gap - 9, y + 13.5); c.stroke();
x += gap;
}
}
}
function drawSpec(c) {
var fx = geo.fx, fy = geo.fy, m = geo.map, k;
label(c, 'G ¬( x < θ₁ ∨ x > θ₂ )', fx, fy, { size: 15, w: 500, color: P.t1 });
label(c, 'always stay between θ₁ and θ₂', fx, fy + 17, { size: 11 });
label(c, 'unknown safety rule (parametric STL)', fx, fy - 20, { size: 11 });
var vt = est ? 'θ₁ = ' + (shownLim || est)[0].toFixed(2) + '     θ₂ = ' + (shownLim || est)[1].toFixed(2) : 'θ₁ = ?     θ₂ = ?';
if (est && phase === 'fit') vt = 'θ₁, θ₂: searching…';
label(c, vt, fx, fy + 39, { size: 13, w: 500, color: P.t1 });
label(c, 'Bayesian optimization over (θ₁, θ₂)', fx, m.y - 9, { size: 11 });
/* how well each candidate rule explains the labeled runs (brighter = better) */
if (heat.acc !== P.acc.join()) { heat = makeHeat(); heatOld = null; }
c.save(); c.imageSmoothingEnabled = true;
if (heatOld && heatT < 1) { c.globalAlpha = 1 - heatT; c.drawImage(heatOld, m.x, m.y, m.s, m.s); }
c.globalAlpha = heatOld && heatT < 1 ? heatT : 1; c.drawImage(heat, m.x, m.y, m.s, m.s); c.restore(); c.globalAlpha = 1;
c.strokeStyle = col(P.hair); c.lineWidth = 1; c.strokeRect(m.x + 0.5, m.y + 0.5, m.s - 1, m.s - 1);
var tu = toU(truth);
c.setLineDash([3, 3]); c.strokeStyle = col(P.warn, 0.7); c.lineWidth = 1; c.beginPath();
c.moveTo(mx(tu[0]), m.y); c.lineTo(mx(tu[0]), m.y + m.s); c.moveTo(m.x, my(tu[1])); c.lineTo(m.x + m.s, my(tu[1])); c.stroke(); c.setLineDash([]);
label(c, 'true', mx(tu[0]) + 4, my(tu[1]) - 5, { size: 11, color: P.t2 });
/* evaluations of this iteration, the running best, and the path of estimates */
var shownN = 0, bestK = -1;
if (bo) {
shownN = phase === 'fit' ? Math.max(0, Math.min(bo.U.length, Math.floor((pt - 0.25) / 0.065) + 1)) : bo.U.length;
for (k = 0; k < shownN; k++) {
circle(c, mx(bo.U[k][0]), my(bo.U[k][1]), 2.1); c.fillStyle = col(P.t1, 0.85); c.fill();
if (bestK < 0 || bo.F[k] < bo.F[bestK] - 1e-12 || (Math.abs(bo.F[k] - bo.F[bestK]) <= 1e-12 && toT(bo.U[k])[1] - toT(bo.U[k])[0] > toT(bo.U[bestK])[1] - toT(bo.U[bestK])[0])) bestK = k;
}
if (phase === 'fit' && shownN > 0 && shownN <= bo.U.length) {
var nu = bo.U[shownN - 1], ag = clamp((pt - 0.25) / 0.065 - (shownN - 1), 0, 1);
c.strokeStyle = col(P.t1, 1 - ag); c.lineWidth = 1.2; circle(c, mx(nu[0]), my(nu[1]), 3 + ag * 8); c.stroke();
}
}
var pts = ppath.slice(0, phase === 'fit' ? ppath.length - 1 : ppath.length);
if (pts.length > 1) {
c.beginPath(); pts.forEach(function (u, j) { if (j) c.lineTo(mx(u[0]), my(u[1])); else c.moveTo(mx(u[0]), my(u[1])); });
c.strokeStyle = col(P.acc, 0.75); c.lineWidth = 1.5; c.stroke();
}
var cu = phase === 'fit' && bestK >= 0 ? bo.U[bestK] : pts[pts.length - 1];
if (cu) {
add(c, true); glow(c, P.sAcc, mx(cu[0]), my(cu[1]), 26, 0.9); add(c, false);
circle(c, mx(cu[0]), my(cu[1]), 4.5); c.strokeStyle = col(P.acc); c.lineWidth = 2; c.stroke();
}
label(c, 'θ₁', m.x + m.s / 2, m.y + m.s + 15, { align: 'center', size: 12, color: P.t1 });
label(c, B1[0].toFixed(1), m.x, m.y + m.s + 15, { size: 11 });
label(c, B1[1].toFixed(1), m.x + m.s, m.y + m.s + 15, { align: 'right', size: 11 });
label(c, 'θ₂', m.x - 8, m.y + m.s / 2 + 4, { align: 'right', size: 12, color: P.t1 });
label(c, B2[1].toFixed(1), m.x - 5, m.y + 10, { align: 'right', size: 11 });
label(c, B2[0].toFixed(1), m.x - 5, m.y + m.s - 2, { align: 'right', size: 11 });
/* labeled runs and this round's verdict */
var sx = geo.stats, sy = m.y + 10, cn = counts(), rs = phase === 'label' ? shownTr.slice(0, revealed).filter(function (q) { return q.safe; }).length : roundSafe;
var rn = phase === 'label' ? revealed : NROLL;
label(c, 'labeled runs', sx, sy, { size: 11 });
label(c, cn[0] + ' safe · ' + cn[1] + ' unsafe', sx, sy + 17, { size: 12.5, w: 500, color: P.t1 });
label(c, 'this round', sx, sy + 44, { size: 11 });
label(c, rs < 0 ? '—' : rs + ' of ' + rn + ' runs safe', sx, sy + 61, { size: 12.5, w: 500, color: P.t1 });
var bw = Math.min(118, d.W - 12 - sx), fr = rs < 0 ? 0 : rs / NROLL;
rrect(c, sx, sy + 71, bw, 6, 3); c.fillStyle = col(P.hair); c.fill();
if (fr > 0) { rrect(c, sx, sy + 71, Math.max(6, bw * fr), 6, 3); c.fillStyle = col(P.acc); c.fill(); }
c.fillStyle = col(P.t1); c.fillRect(sx + bw * 0.9 - 0.5, sy + 67, 1.5, 14);
label(c, 'stop at 90% safe', sx, sy + 96, { size: 11 });
if (phase === 'done' && conv) {
c.strokeStyle = col(P.acc); c.lineWidth = 2.2; c.beginPath(); c.moveTo(sx + 1, sy + 117); c.lineTo(sx + 5, sy + 121); c.lineTo(sx + 12, sy + 112); c.stroke();
label(c, 'converged', sx + 18, sy + 121, { size: 12.5, w: 600, color: P.t1 });
}
/* summary */
var st;
if (phase === 'done' && est) st = 'learned (' + est[0].toFixed(2) + ', ' + est[1].toFixed(2) + ')  ·  true (' + truth[0].toFixed(2) + ', ' + truth[1].toFixed(2) + ')';
else if (phase === 'intro') st = 'start: 20 runs labeled by an expert';
else st = phase === 'fit' ? 'fitting the limits to the labeled runs' : phase === 'train' ? 'retraining the policy under the new limits' : 'the expert labels each new run';
label(c, st, geo.narrow ? geo.fx : geo.fx, geo.sum, { size: geo.narrow ? 11 : 11.5, w: phase === 'done' ? 600 : 400, color: phase === 'done' ? P.t1 : P.t2 });
}
d.draw = function () {
d.clear();
if (!geo) return;
var c = d.ctx;
drawWorld(c); drawPills(c); drawSpec(c);
};
d.still = function () {
newRun(false, truth[0] === PAPER[0] && truth[1] === PAPER[1] ? SEED : null);
while (it < MAXIT) { doFit(); shownLim = est.slice(); limFrom = null; limT = 1; shownTr = doLabel(); data = data.concat(shownTr); if (roundSafe >= 9) break; }
conv = roundSafe >= 9; phase = 'done'; pt = 0; revealed = NROLL; oldTr = []; heatT = 1; heat = makeHeat();
pol = nominal(est); polFrom = pol; polTo = pol; polT = 1;
trail = []; for (var k = 0; k < 28; k++) { var a = 0.6 + k * 0.03; trail.push([clamp(RC * Math.cos(a), pol[0], pol[1]), RC * Math.sin(a)]); }
hud(); d.draw();
};
d.act = function () { newRun(false, truth[0] === PAPER[0] && truth[1] === PAPER[1] ? SEED : null); };
function nearLine(p) {
if (!geo) return -1;
var wd = geo.world;
if (p[1] < wd.y || p[1] > wd.y + wd.h) return -1;
for (var i = 0; i < 2; i++) if (Math.abs(p[0] - wx(truth[i])) < 11) return i;
return -1;
}
d.cv.addEventListener('pointerdown', function (e) {
var i = nearLine(d.pt(e));
if (i < 0) return;
dragging = i; d.cv.setPointerCapture(e.pointerId); e.preventDefault(); d.cv.style.cursor = 'ew-resize';
if (!d.run) d.paint();
});
d.cv.addEventListener('pointermove', function (e) {
var p = d.pt(e);
if (dragging >= 0) {
var v = (p[0] - geo.cx) / geo.sc;
truth[dragging] = dragging ? clamp(v, 0.6, 1.4) : clamp(v, -1.4, -0.6);
if (!d.run) d.paint();
} else {
var h = nearLine(p);
if (h !== hoverLine) { hoverLine = h; d.cv.style.cursor = h >= 0 ? 'ew-resize' : ''; if (!d.run) d.paint(); }
}
});
function up() { if (dragging >= 0) { dragging = -1; userRule = true; d.cv.style.cursor = ''; newRun(false); if (!d.run) d.paint(true); } }
d.cv.addEventListener('pointerup', up);
d.cv.addEventListener('pointercancel', up);
d.cv.addEventListener('pointerleave', function () { if (hoverLine >= 0 && dragging < 0) { hoverLine = -1; if (!d.run) d.paint(); } });
truth = PAPER.slice();
newRun(false, SEED);
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
