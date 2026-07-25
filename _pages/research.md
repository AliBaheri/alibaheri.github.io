---
layout: page
permalink: /research/
title: research
description: Building autonomous systems that can be trusted &mdash; safe reinforcement learning, safety validation, and calibrated uncertainty for aviation, robotics, and clinical decision support.
nav: true
nav_order: 2
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
</style>

<div class="rintro" markdown="1">
Autonomous systems increasingly depend on learned components &mdash; perception models,
control policies, and now foundation models. These components are capable but opaque:
they fail in ways their designers did not anticipate, and they offer no native account
of their own reliability. My research asks what it takes to deploy them where failure
is not an option, in aviation and airspace operations, robots working around people,
and clinical decision support.

The work follows four connected pillars: the **geometric foundations** that make
guarantees tractable in the first place; **learning policies that respect safety
requirements** even when those requirements are never fully specified; **quantifying
uncertainty** so a system knows when it should not be trusted; and **finding failures
before deployment**, efficiently enough to be practical. This agenda is supported by
NSF, the FAA, and NASA.
</div>

<div class="tgrid">
<a class="tcard" href="#geometry">
<div class="ci"><i class="fas fa-shapes" aria-hidden="true"></i></div>
<div class="cn">01</div>
<div class="ct">Geometric Foundations</div>
<div class="cc">9 selected papers</div>
</a>
<a class="tcard" href="#safe-rl">
<div class="ci"><i class="fas fa-robot" aria-hidden="true"></i></div>
<div class="cn">02</div>
<div class="ct">Safe Reinforcement Learning</div>
<div class="cc">8 selected papers</div>
</a>
<a class="tcard" href="#uncertainty">
<div class="ci"><i class="fas fa-bullseye" aria-hidden="true"></i></div>
<div class="cn">03</div>
<div class="ct">Uncertainty Quantification</div>
<div class="cc">5 selected papers</div>
</a>
<a class="tcard" href="#validation">
<div class="ci"><i class="fas fa-clipboard-check" aria-hidden="true"></i></div>
<div class="cn">04</div>
<div class="ct">Safety Validation</div>
<div class="cc">7 selected papers</div>
</a>
</div>

<div class="theme" id="geometry">
<div class="watermark" aria-hidden="true">01</div>
<div class="thead">
<div class="ticon"><i class="fas fa-shapes" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Geometric Foundations for Trustworthy Learning</h2>
<div class="tsub">Optimal transport and structure-preserving generative models</div>
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
<ul class="papers">
<li><span class="pv">L-CSS</span><span class="pt"><a href="https://ieeexplore.ieee.org/document/11563844" target="_blank">Blending Optimism and Pessimism via Wasserstein Barycenters for Continuous Control</a></span><span class="py">2026</span></li>
<li><span class="pv">CDC</span><span class="pt"><a href="https://arxiv.org/abs/2607.14291" target="_blank">Wasserstein Stability of Contracting Flows: Effective Rates, Euler Self-Correction, and Noise Tightening</a></span><span class="py">2026</span></li>
<li><span class="pv">L4DC</span><span class="pt">WAVE: Wasserstein Adaptive Value Estimation for Actor-Critic Reinforcement Learning</span><span class="py">2025</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2506.12497" target="_blank">Wasserstein-Barycenter Consensus for Cooperative Multi-Agent Reinforcement Learning</a></span><span class="py">2025</span></li>
<li><span class="pv">ECC</span><span class="pt">Metriplectic Conditional Flow Matching for Structure-Preserving Dynamics Learning</span><span class="py">2026</span></li>
<li><span class="pv">NeuS</span><span class="pt"><a href="https://arxiv.org/abs/2602.02009" target="_blank">Logic-Guided Vector Fields for Constrained Generative Modeling</a></span><span class="py">2026</span></li>
<li><span class="pv">ICLR</span><span class="pt">Geometry-Grounded Flow Matching on Compact Manifolds</span><span class="py">2026</span></li>
<li><span class="pv">ACC</span><span class="pt"><a href="https://arxiv.org/abs/2509.14521" target="_blank">Geometry-Aware Decentralized Sinkhorn for Wasserstein Barycenters</a></span><span class="py">2026</span></li>
<li><span class="pv">NeurIPS</span><span class="pt">Understanding Reward Ambiguity Through Optimal Transport Theory in Inverse Reinforcement Learning</span><span class="py">2023</span></li>
</ul>
</div>

<div class="theme" id="safe-rl">
<div class="watermark" aria-hidden="true">02</div>
<div class="thead">
<div class="ticon"><i class="fas fa-robot" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Safe and Constraint-Aware Reinforcement Learning</h2>
<div class="tsub">Policies that carry a safety argument, not just good average performance</div>
</div>
</div>
<p class="tbody">Most work on safe reinforcement learning assumes the constraint is handed
to you in closed form. In deployment it rarely is: the specification is partial,
expressed in temporal logic, implied by human corrections, or buried in a dataset of
demonstrations of unknown quality. My work learns the policy and the constraint
<em>together</em> &mdash; inferring unknown temporal specifications during training,
refining behavior from human feedback, and enforcing safety through learned
Lyapunov&ndash;barrier certificates that come with stability guarantees. A recurring
device is hierarchy: decomposing long-horizon tasks so that safety can be reasoned
about at the level of abstraction where it is actually specified.</p>
<ul class="papers">
<li><span class="pv">OJ-CSYS</span><span class="pt"><a href="https://ieeexplore.ieee.org/abstract/document/10569078" target="_blank">Concurrent Learning of Control Policy and Unknown Safety Specifications in Reinforcement Learning</a></span><span class="py">2024</span></li>
<li><span class="pv">RICO</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2666720725000426" target="_blank">Distributionally Robust Lyapunov-Barrier Networks for Safe and Stable Control Under Uncertainty</a></span><span class="py">2025</span></li>
<li><span class="pv">RSS</span><span class="pt"><a href="https://arxiv.org/abs/2506.14058" target="_blank">Implicit Constraint-Aware Off-Policy Correction for Offline Reinforcement Learning</a></span><span class="py">2025</span></li>
<li><span class="pv">MDPI</span><span class="pt"><a href="https://www.mdpi.com/2227-7390/13/1/149" target="_blank">Multilevel Constrained Bandits: A Hierarchical Upper Confidence Bound Approach with Safety Guarantees</a></span><span class="py">2025</span></li>
<li><span class="pv">NeSy</span><span class="pt"><a href="https://openreview.net/forum?id=tXOU6EULup" target="_blank">Hierarchical Neuro-Symbolic Decision Transformer</a></span><span class="py">2025</span></li>
<li><span class="pv">ACC</span><span class="pt">Density-Ratio Weighted Behavioral Cloning: Learning Control Policies from Corrupted Datasets</span><span class="py">2026</span></li>
<li><span class="pv">ICAPS</span><span class="pt">Policy Refinement with Human Feedback for Safe Reinforcement Learning</span><span class="py">2023</span></li>
<li><span class="pv">EAAI</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/abs/pii/S0952197624010698" target="_blank">A Survey on Reinforcement Learning in Aviation Applications</a></span><span class="py">2024</span></li>
</ul>
</div>

<div class="theme" id="uncertainty">
<div class="watermark" aria-hidden="true">03</div>
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
flat, exchangeable data. I extend it to settings with real structure &mdash;
hierarchical data with group-level effects, and predictions living on manifolds
&mdash; while preserving coverage. A companion line turns disagreement among ensemble
members into an online signal for adapting the safety margin of a model-predictive
controller. Applications run from aviation autonomy to clinical decision support.</p>
<ul class="papers">
<li><span class="pv">OJ-CSYS</span><span class="pt">How Much Do Your Models Disagree? Adaptive MPC Safety from Ensemble Uncertainty</span><span class="py">2026</span></li>
<li><span class="pv">RAM</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2590037425000536" target="_blank">Conformal Prediction Across Scales: Finite-Sample Coverage with Hierarchical Efficiency</a></span><span class="py">2025</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2602.16015" target="_blank">Geometry-Aware Uncertainty Quantification via Conformal Prediction on Manifolds</a></span><span class="py">2026</span></li>
<li><span class="pv">AAAI</span><span class="pt"><a href="https://arxiv.org/abs/2601.01223" target="_blank">Adaptive Conformal Prediction via Bayesian Uncertainty Weighting for Hierarchical Healthcare Data</a></span><span class="py">2026</span></li>
<li><span class="pv">Sci. Rep.</span><span class="pt">A Hierarchical Conformal Framework for Uncertainty-Aware Length of Stay Prediction in Multi-Hospital Settings</span><span class="py">2026</span></li>
</ul>
</div>

<div class="theme" id="validation">
<div class="watermark" aria-hidden="true">04</div>
<div class="thead">
<div class="ticon"><i class="fas fa-clipboard-check" aria-hidden="true"></i></div>
<div>
<h2 class="ttitle">Safety Validation of Learning-Enabled Autonomous Systems</h2>
<div class="tsub">Finding the failures before deployment does</div>
</div>
</div>
<p class="tbody">A learned controller can pass millions of random simulation trials and still
fail catastrophically on the rare input that matters. Exhaustive verification is out
of reach, and high-fidelity simulation is far too expensive to search with. I develop
<em>multi-fidelity falsification</em>: methods that search broadly using cheap,
approximate simulators and spend expensive high-fidelity evaluations only where a
failure looks likely, with the fidelity level itself treated as a decision variable.
Related work asks how much simulator fidelity is actually required to certify a given
property, and develops stratified temporal logics for requirements that span scales.
This thread underpins my NSF- and FAA-funded projects and was the subject of my
AAAI New Faculty Highlights talk.</p>
<ul class="papers">
<li><span class="pv">IEEE Access</span><span class="pt"><a href="https://ieeexplore.ieee.org/abstract/document/11488849" target="_blank">Efficient Counterexample Generation for Control Systems Using Multi-Fidelity Bayesian Optimization</a></span><span class="py">2026</span></li>
<li><span class="pv">Logics</span><span class="pt"><a href="https://www.mdpi.com/2813-0405/3/2/5" target="_blank">Multi-Fidelity Temporal Reasoning: A Stratified Logic for Cross-Scale System Specifications</a></span><span class="py">2025</span></li>
<li><span class="pv">IEEE Access</span><span class="pt"><a href="https://ieeexplore.ieee.org/document/10620179" target="_blank">BEACON: A Bayesian Evolutionary Approach for Counterexample Generation of Control Systems</a></span><span class="py">2024</span></li>
<li><span class="pv">AI Mag.</span><span class="pt">Exploring the Role of Simulator Fidelity in the Safety Validation of Learning-Enabled Autonomous Systems</span><span class="py">2023</span></li>
<li><span class="pv">ECC</span><span class="pt">Falsification of Learning-Based Controllers through Multi-Fidelity Bayesian Optimization</span><span class="py">2023</span></li>
<li><span class="pv">AAAI</span><span class="pt">Safety Validation of Learning-Based Autonomous Systems: A Multi-Fidelity Approach</span><span class="py">2023</span></li>
<li><span class="pv">arXiv</span><span class="pt"><a href="https://arxiv.org/abs/2305.06111" target="_blank">Joint Falsification and Fidelity Settings Optimization for Validation of Safety-Critical Systems: A Theoretical Analysis</a></span><span class="py">2023</span></li>
</ul>
</div>

<div class="rfund" markdown="1">

## Funding

<ul>
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
