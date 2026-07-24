---
layout: page
permalink: /research/
title: research
description: My group works on decision-making under uncertainty for safety-critical autonomous systems, at the intersection of reinforcement learning, control theory, and applied probability.
nav: true
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
I build decision-making methods for systems that have to be trusted: aircraft, robots,
and clinical decision support. Two ideas run through nearly all of it. The first is
**geometry** — treating policies, beliefs, and dynamics as objects on a metric or
manifold structure rather than as flat vectors, which makes optimal transport and
flow matching natural tools. The second is **hierarchy** — reasoning across levels
of fidelity, abstraction, and scale, so that expensive computation and strong
guarantees are spent where they matter.
</div>

<div class="theme">
<div class="tnum">01</div>
<h2 class="ttitle">Optimal Transport and Distributional Geometry for Decision-Making</h2>
<div class="tsub">Wasserstein methods for reinforcement learning, control, and coordination</div>
<p class="tbody">Classical reinforcement learning compares policies and value estimates
pointwise. My work treats them as <em>probability distributions</em> and uses the
geometry of optimal transport to compare, average, and constrain them. Wasserstein
distances give a principled notion of how far apart two agents' beliefs are;
barycenters give a principled way to merge them. This yields algorithms for
risk-sensitive value estimation, cooperative multi-agent consensus, trust-region
updates that respect distributional geometry, and federated learning where agents
share structure rather than raw data.</p>
<ul class="papers">
<li><span class="pv">L-CSS</span><span class="pt"><a href="https://ieeexplore.ieee.org/document/11563844" target="_blank">Blending Optimism and Pessimism via Wasserstein Barycenters for Continuous Control</a></span><span class="py">2026</span></li>
<li><span class="pv">CDC</span><span class="pt"><a href="https://arxiv.org/abs/2607.14291" target="_blank">Wasserstein Stability of Contracting Flows: Effective Rates, Euler Self-Correction, and Noise Tightening</a></span><span class="py">2026</span></li>
<li><span class="pv">ACC</span><span class="pt"><a href="https://arxiv.org/abs/2509.14521" target="_blank">Geometry-Aware Decentralized Sinkhorn for Wasserstein Barycenters</a></span><span class="py">2026</span></li>
<li><span class="pv">L4DC</span><span class="pt"><a href="https://arxiv.org/abs/2601.00309" target="_blank">Can Optimal Transport Improve Federated Inverse Reinforcement Learning?</a></span><span class="py">2026</span></li>
<li><span class="pv">L4DC</span><span class="pt">WAVE: Wasserstein Adaptive Value Estimation for Actor-Critic Reinforcement Learning</span><span class="py">2025</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2506.12497" target="_blank">Wasserstein-Barycenter Consensus for Cooperative Multi-Agent Reinforcement Learning</a></span><span class="py">2025</span></li>
<li><span class="pv">NeurIPS</span><span class="pt">Understanding Reward Ambiguity Through Optimal Transport Theory in Inverse Reinforcement Learning</span><span class="py">2023</span></li>
</ul>
</div>

<div class="theme">
<div class="tnum">02</div>
<h2 class="ttitle">Structure-Preserving and Constrained Generative Modeling</h2>
<div class="tsub">Flow matching that respects physics, geometry, and logic</div>
<p class="tbody">Generative models are increasingly used as simulators and dynamics models
for physical systems, but an unconstrained model will happily produce trajectories
that violate conservation laws, leave the manifold, or break a specification. I
develop flow-matching methods that build these constraints into the vector field
itself: metriplectic structure for dissipative dynamics, Riemannian geometry for
data on manifolds, and temporal-logic guidance for constrained generation. A related
thread asks a diagnostic question, namely what a trained neural PDE solver has
actually learned.</p>
<ul class="papers">
<li><span class="pv">ECC</span><span class="pt">Metriplectic Conditional Flow Matching for Structure-Preserving Dynamics Learning</span><span class="py">2026</span></li>
<li><span class="pv">NeuS</span><span class="pt"><a href="https://arxiv.org/abs/2602.02009" target="_blank">Logic-Guided Vector Fields for Constrained Generative Modeling</a></span><span class="py">2026</span></li>
<li><span class="pv">ICLR</span><span class="pt">Geometry-Grounded Flow Matching on Compact Manifolds</span><span class="py">2026</span></li>
<li><span class="pv">ICLR</span><span class="pt">What Does a Neural PDE Solver Really Learn? A Residual-Spectrum Diagnostic</span><span class="py">2026</span></li>
<li><span class="pv">RLC</span><span class="pt"><a href="https://arxiv.org/abs/2606.23933" target="_blank">Flow-Corrected Thompson Sampling for Non-Stationary Contextual Bandits</a></span><span class="py">2026</span></li>
<li><span class="pv">CCS</span><span class="pt">When Does Multi-Agent Language-Model Debate Converge? A Bifurcation on the Probability Simplex</span><span class="py">2026</span></li>
</ul>
</div>

<div class="theme">
<div class="tnum">03</div>
<h2 class="ttitle">Safe and Constraint-Aware Reinforcement Learning</h2>
<div class="tsub">Learning policies when the safety specification is unknown or implicit</div>
<p class="tbody">Most safe-RL work assumes the constraint is handed to you. In practice the
specification is partially known, expressed in temporal logic, implied by human
feedback, or buried in a dataset of demonstrations. My work learns the policy and
the constraint together: inferring unknown temporal specifications during training,
refining policies from human feedback, enforcing safety through learned
Lyapunov-barrier certificates, and correcting for distribution shift in offline
data. Hierarchy is a recurring device, decomposing long-horizon problems so that
safety can be reasoned about at the right level of abstraction.</p>
<ul class="papers">
<li><span class="pv">OJ-CSYS</span><span class="pt"><a href="https://ieeexplore.ieee.org/abstract/document/10569078" target="_blank">Concurrent Learning of Control Policy and Unknown Safety Specifications in Reinforcement Learning</a></span><span class="py">2024</span></li>
<li><span class="pv">RSS</span><span class="pt"><a href="https://arxiv.org/abs/2506.14058" target="_blank">Implicit Constraint-Aware Off-Policy Correction for Offline Reinforcement Learning</a></span><span class="py">2025</span></li>
<li><span class="pv">RICO</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2666720725000426" target="_blank">Distributionally Robust Lyapunov-Barrier Networks for Safe and Stable Control Under Uncertainty</a></span><span class="py">2025</span></li>
<li><span class="pv">MDPI</span><span class="pt"><a href="https://www.mdpi.com/2227-7390/13/1/149" target="_blank">Multilevel Constrained Bandits: A Hierarchical Upper Confidence Bound Approach with Safety Guarantees</a></span><span class="py">2025</span></li>
<li><span class="pv">NeSy</span><span class="pt"><a href="https://openreview.net/forum?id=tXOU6EULup" target="_blank">Hierarchical Neuro-Symbolic Decision Transformer</a></span><span class="py">2025</span></li>
<li><span class="pv">ACC</span><span class="pt">Density-Ratio Weighted Behavioral Cloning: Learning Control Policies from Corrupted Datasets</span><span class="py">2026</span></li>
<li><span class="pv">EAAI</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/abs/pii/S0952197624010698" target="_blank">A Survey on Reinforcement Learning in Aviation Applications</a></span><span class="py">2024</span></li>
</ul>
</div>

<div class="theme">
<div class="tnum">04</div>
<h2 class="ttitle">Validation and Uncertainty Quantification for Learning-Enabled Systems</h2>
<div class="tsub">Multi-fidelity falsification, conformal prediction, and calibrated confidence</div>
<p class="tbody">Before a learning-enabled system is deployed in an aircraft or a hospital,
someone has to answer two questions: where does it fail, and how much should we trust
any single prediction? For the first, I develop multi-fidelity falsification methods
that spend cheap simulation budget broadly and expensive high-fidelity budget only
where failures are likely. For the second, I extend conformal prediction to
hierarchical and manifold-valued data, producing finite-sample coverage guarantees
in settings where the data has structure that flat methods ignore. Applications
span aviation autonomy and clinical decision support.</p>
<ul class="papers">
<li><span class="pv">OJ-CSYS</span><span class="pt">How Much Do Your Models Disagree? Adaptive MPC Safety from Ensemble Uncertainty</span><span class="py">2026</span></li>
<li><span class="pv">IEEE Access</span><span class="pt"><a href="https://ieeexplore.ieee.org/abstract/document/11488849" target="_blank">Efficient Counterexample Generation for Control Systems Using Multi-Fidelity Bayesian Optimization</a></span><span class="py">2026</span></li>
<li><span class="pv">RAM</span><span class="pt"><a href="https://www.sciencedirect.com/science/article/pii/S2590037425000536" target="_blank">Conformal Prediction Across Scales: Finite-Sample Coverage with Hierarchical Efficiency</a></span><span class="py">2025</span></li>
<li><span class="pv">Logics</span><span class="pt"><a href="https://www.mdpi.com/2813-0405/3/2/5" target="_blank">Multi-Fidelity Temporal Reasoning: A Stratified Logic for Cross-Scale System Specifications</a></span><span class="py">2025</span></li>
<li><span class="pv">ICML</span><span class="pt"><a href="https://arxiv.org/abs/2602.16015" target="_blank">Geometry-Aware Uncertainty Quantification via Conformal Prediction on Manifolds</a></span><span class="py">2026</span></li>
<li><span class="pv">IEEE Access</span><span class="pt"><a href="https://ieeexplore.ieee.org/document/10620179" target="_blank">BEACON: A Bayesian Evolutionary Approach for Counterexample Generation of Control Systems</a></span><span class="py">2024</span></li>
<li><span class="pv">AI Mag.</span><span class="pt">Exploring the Role of Simulator Fidelity in the Safety Validation of Learning-Enabled Autonomous Systems</span><span class="py">2023</span></li>
<li><span class="pv">ECC</span><span class="pt">Falsification of Learning-Based Controllers through Multi-Fidelity Bayesian Optimization</span><span class="py">2023</span></li>
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
