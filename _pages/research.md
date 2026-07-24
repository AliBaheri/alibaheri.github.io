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
     <ul class="papers"> and edit the venue, title, link, and year. -->

<style>
.rintro {
  font-size: 1.02rem; line-height: 1.65; margin-bottom: 2.6rem;
  padding-left: 1rem; border-left: 3px solid var(--global-theme-color);
}
.theme { position: relative; padding-left: 3.4rem; margin-bottom: 3rem; }
.theme .tnum {
  position: absolute; left: 0; top: .15rem;
  width: 2.4rem; height: 2.4rem; border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: .85rem; font-weight: 700; letter-spacing: .02em; color: #fff;
  background: var(--global-theme-color);
  background: linear-gradient(135deg, var(--global-theme-color),
    color-mix(in srgb, var(--global-theme-color) 60%, #000));
  box-shadow: 0 2px 6px color-mix(in srgb, var(--global-theme-color) 35%, transparent);
}
.theme .ttitle { margin: 0 0 .15rem; font-size: 1.3rem; line-height: 1.3; }
.theme .tsub {
  font-size: .76rem; text-transform: uppercase; letter-spacing: .07em;
  color: var(--global-theme-color); margin-bottom: .9rem;
}
.theme .tbody { font-size: .95rem; line-height: 1.65; margin-bottom: 1.1rem; }
.theme .papers { list-style: none; padding: 0; margin: 0; }
.theme .papers li {
  display: flex; align-items: baseline; gap: .7rem;
  padding: .42rem 0 .42rem .55rem;
  border-top: 1px solid color-mix(in srgb, var(--global-text-color) 12%, transparent);
  font-size: .88rem; transition: background .18s ease;
}
.theme .papers li:last-child {
  border-bottom: 1px solid color-mix(in srgb, var(--global-text-color) 12%, transparent);
}
.theme .papers li:hover {
  background: color-mix(in srgb, var(--global-theme-color) 7%, transparent);
}
.theme .papers .pv {
  flex: 0 0 4.6rem; font-size: .72rem; font-weight: 600;
  color: var(--global-theme-color); text-transform: uppercase; letter-spacing: .03em;
}
.theme .papers .pt { flex: 1; }
.theme .papers .py { flex: 0 0 auto; font-size: .78rem; color: var(--global-text-color-light); }
.rfund { margin-top: 3rem; }
.rfund ul { list-style: none; padding: 0; }
.rfund li {
  padding: .5rem 0 .5rem .9rem; font-size: .9rem;
  border-left: 2px solid color-mix(in srgb, var(--global-theme-color) 40%, transparent);
  margin-bottom: .45rem;
}
.rfund .agency { font-weight: 600; color: var(--global-theme-color); }
.rfund .role { font-size: .78rem; color: var(--global-text-color-light); }

@media (max-width: 576px) {
  .theme { padding-left: 0; }
  .theme .tnum { position: static; margin-bottom: .6rem; }
  .theme .papers li { flex-wrap: wrap; gap: .3rem .6rem; }
  .theme .papers .pv { flex: 0 0 auto; }
}
@media (prefers-reduced-motion: reduce) {
  .theme .papers li { transition: none; }
}
</style>

<div class="rintro" markdown="1">
Autonomous systems increasingly depend on learned components &mdash; perception models,
control policies, and now foundation models. These components are capable but opaque:
they fail in ways their designers did not anticipate, and they offer no native account
of their own reliability. My research asks what it takes to deploy them where failure
is not an option, in aviation and airspace operations, robots working around people,
and clinical decision support.

The work follows four connected pillars: **learning policies that respect safety
requirements** even when those requirements are never fully specified; **finding
failures before deployment**, efficiently enough to be practical; **quantifying
uncertainty** so a system knows when it should not be trusted; and developing the
**geometric foundations** that make these guarantees tractable at scale. This agenda
is supported by NSF, the FAA, and NASA.
</div>

<div class="theme">
<div class="tnum">01</div>
<h2 class="ttitle">Safe and Constraint-Aware Reinforcement Learning</h2>
<div class="tsub">Policies that carry a safety argument, not just good average performance</div>
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

<div class="theme">
<div class="tnum">02</div>
<h2 class="ttitle">Safety Validation of Learning-Enabled Autonomous Systems</h2>
<div class="tsub">Finding the failures before deployment does</div>
<p class="tbody">A learned controller can pass millions of random simulation trials and still
fail catastrophically on the rare input that matters. Exhaustive verification is out
of reach, and high-fidelity simulation is far too expensive to search with. I develop
<em>multi-fidelity falsification</em>: methods that search broadly using cheap,
approximate simulators and spend expensive high-fidelity evaluations only where a
failure looks likely, with the fidelity level itself treated as a decision variable.
Related work asks how much simulator fidelity is actually needed to certify a given
property, and develops stratified temporal logics for stating requirements that span
scales. This thread underpins my NSF and FAA funded projects and was the subject of my
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

<div class="theme">
<div class="tnum">03</div>
<h2 class="ttitle">Uncertainty Quantification and Calibrated Confidence</h2>
<div class="tsub">Systems that know when they should not be trusted</div>
<p class="tbody">Trustworthiness requires more than average accuracy: a deployed system needs
a defensible account of its own uncertainty, and a controller needs to become more
conservative exactly when its models are least reliable. Conformal prediction offers
distribution-free, finite-sample coverage guarantees, but standard formulations assume
flat, exchangeable data. I extend it to settings with real structure &mdash;
hierarchical data with group-level effects, and predictions living on manifolds
&mdash; while preserving coverage. A companion line turns ensemble disagreement into
an online signal for adapting the safety margin of a model-predictive controller.
Applications run from aviation autonomy to clinical decision support.</p>
<ul class="papers">
<li><span class="pv">OJ-CSYS</span><span class="pt">How Much Do Your Models Disagree? Adaptive MPC Safety from Ensemble Uncertainty</span><span class="py">2026</span></li>
<li><span class="pv">RAM</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2590037425000536" target="_blank">Conformal Prediction Across Scales: Finite-Sample Coverage with Hierarchical Efficiency</a></span><span class="py">2025</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2602.16015" target="_blank">Geometry-Aware Uncertainty Quantification via Conformal Prediction on Manifolds</a></span><span class="py">2026</span></li>
<li><span class="pv">AAAI</span><span class="pt"><a href="https://arxiv.org/abs/2601.01223" target="_blank">Adaptive Conformal Prediction via Bayesian Uncertainty Weighting for Hierarchical Healthcare Data</a></span><span class="py">2026</span></li>
<li><span class="pv">Sci. Rep.</span><span class="pt">A Hierarchical Conformal Framework for Uncertainty-Aware Length of Stay Prediction in Multi-Hospital Settings</span><span class="py">2026</span></li>
</ul>
</div>

<div class="theme">
<div class="tnum">04</div>
<h2 class="ttitle">Geometric Foundations for Trustworthy Learning</h2>
<div class="tsub">Optimal transport and structure-preserving generative models</div>
<p class="tbody">The guarantees above ultimately rest on comparing and combining probability
distributions, which is exactly what optimal transport is built for. Treating policies
and value estimates as distributions rather than points yields risk-sensitive value
estimation, principled consensus among cooperating agents through Wasserstein
barycenters, and trust-region updates that respect distributional geometry. A parallel
line builds structure into generative dynamics models: metriplectic flow matching that
respects dissipative physics, flow matching on manifolds, and temporal-logic guidance
for constrained generation. The motivation is reliability rather than elegance &mdash;
a learned dynamics model that violates conservation laws or leaves the feasible set
cannot support a safety argument downstream.</p>
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
