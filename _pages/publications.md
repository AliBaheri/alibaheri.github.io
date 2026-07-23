---
layout: page
permalink: /publications/
title: publications
description: Publications since 2023, in reverse chronological order. For the complete list, see my <a href="https://scholar.google.com/citations?user=MhIEockAAAAJ" target="_blank">Google Scholar</a> profile or <a href="/assets/pdf/cv_academic.pdf" target="_blank">CV</a>.
nav: true
---

<!-- Plain HTML on purpose: no Jekyll plugins required, so this builds on
     GitHub Pages with no extra setup. The BibTeX source of record lives in
     _bibliography/papers.bib.
     To add a paper: copy one list item below and edit the text.
     data-topics accepts: ot rl uq gen (space separated, or empty).
     To flag a spotlight or oral, add class "highlight" plus
     data-award="spotlight" or "oral" on the list item, and drop the matching
     span.pub-award into the title div. -->

<style>
/* ---------- filter bar ---------- */
.pub-filter { margin-bottom: 1.5rem; }
.pub-filter input {
  width: 100%; padding: .5rem .75rem; margin-bottom: .75rem;
  border: 1px solid var(--global-text-color-light); border-radius: 4px;
  background: var(--global-bg-color); color: var(--global-text-color);
  font-size: .95rem;
}
.pub-filter input:focus { outline: none; border-color: var(--global-theme-color); }
.pub-chips { display: flex; flex-wrap: wrap; gap: .4rem; }
.pub-chips button {
  font-size: .8rem; padding: .25rem .8rem; cursor: pointer;
  border: 1px solid var(--global-text-color-light); border-radius: 4px;
  background: transparent; color: var(--global-text-color);
  transition: all .18s ease;
}
.pub-chips button:hover { border-color: var(--global-theme-color); color: var(--global-theme-color); }
.pub-chips button.active {
  background: var(--global-theme-color); border-color: var(--global-theme-color); color: #fff;
}
.pub-chips button.chip-award i { font-size: .72rem; margin-right: .3rem; }
.pub-count { font-size: .8rem; color: var(--global-text-color-light); margin-top: 1.5rem; }

/* ---------- highlighted papers ---------- */
.publications ol.bibliography li.highlight {
  position: relative;
  padding: .5rem .5rem .5rem 1.1rem;
  margin: .35rem 0 .9rem;
  border-radius: 0 6px 6px 0;
  background: linear-gradient(
    90deg,
    color-mix(in srgb, var(--global-theme-color) 8%, transparent),
    transparent 60%);
  transition: background .25s ease, transform .25s ease;
}
.publications ol.bibliography li.highlight::before {
  content: ""; position: absolute; left: 0; top: .3rem; bottom: .3rem;
  width: 3px; border-radius: 3px; background: var(--global-theme-color);
}
.publications ol.bibliography li.highlight:hover {
  background: linear-gradient(
    90deg,
    color-mix(in srgb, var(--global-theme-color) 15%, transparent),
    transparent 70%);
  transform: translateX(2px);
}

/* ---------- award pill ---------- */
.pub-award {
  display: inline-flex; align-items: center; gap: .32rem;
  vertical-align: middle; margin-left: .55rem;
  padding: .1rem .6rem;
  font-size: .66rem; font-weight: 600; letter-spacing: .05em;
  text-transform: uppercase; white-space: nowrap;
  color: #fff; border-radius: 999px;
  background: var(--global-theme-color);
  background: linear-gradient(135deg,
    var(--global-theme-color),
    color-mix(in srgb, var(--global-theme-color) 62%, #000));
  box-shadow: 0 1px 3px color-mix(in srgb, var(--global-theme-color) 40%, transparent);
}
.pub-award i { font-size: .68rem; }

@media (prefers-reduced-motion: reduce) {
  .publications ol.bibliography li.highlight,
  .publications ol.bibliography li.highlight:hover { transition: none; transform: none; }
}
</style>

<div class="pub-filter">
  <input type="text" id="pub-search" placeholder="Search titles, venues, coauthors" aria-label="Search publications">
  <div class="pub-chips" id="pub-chips">
    <button class="active" data-topic="all">All</button>
    <button class="chip-award" data-topic="award"><i class="fas fa-star" aria-hidden="true"></i>Highlights</button>
    <button data-topic="ot">Optimal transport</button>
    <button data-topic="rl">RL</button>
    <button data-topic="uq">UQ</button>
    <button data-topic="gen">Generative AI</button>
  </div>
</div>

<div class="publications">

<div class="year-group" data-year="2026">
<h2 class="year">2026</h2>
<ol class="bibliography">
<li class="pub" data-topics="uq">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">OJ-CSYS</abbr></div>
 <div id="baheri2026disagree" class="col-sm-8">
  <div class="title">How Much Do Your Models Disagree? Adaptive MPC Safety from Ensemble Uncertainty</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>IEEE Open Journal of Control Systems</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="uq">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">Sci. Rep.</abbr></div>
 <div id="amirishahbazi2026conformal" class="col-sm-8">
  <div class="title">A Hierarchical Conformal Framework for Uncertainty-Aware Length of Stay Prediction in Multi-Hospital Settings</div>
  <div class="author">Amiri Shahbazi, Marzieh, <em>Baheri, Ali</em>, and Azadeh-Fard, Nasibeh</div>
  <div class="periodical"><em>Scientific Reports</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">L-CSS</abbr></div>
 <div id="shahrooei2026blending" class="col-sm-8">
  <div class="title">Blending Optimism and Pessimism via Wasserstein Barycenters for Continuous Control</div>
  <div class="author">Shahrooei, Zahra, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>IEEE Control Systems Letters</em> 2026</div>
  <div class="links">
 <a href="https://ieeexplore.ieee.org/document/11563844" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">IEEE Access</abbr></div>
 <div id="shahrooei2026efficient" class="col-sm-8">
  <div class="title">Efficient Counterexample Generation for Control Systems Using Multi-Fidelity Bayesian Optimization</div>
  <div class="author">Shahrooei, Zahra, <a href="https://scholar.google.com/citations?user=cAy9G6oAAAAJ" target="_blank">Kochenderfer, Mykel J.</a>, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>IEEE Access</em> 2026</div>
  <div class="links">
 <a href="https://ieeexplore.ieee.org/abstract/document/11488849" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"></div>
 <div id="nau2026fairness" class="col-sm-8">
  <div class="title">Fairness Without Discrimination: Individually Fair Outcomes in the Kidney Exchange Problem</div>
  <div class="author">Nau, C., McConky, K., Alm, Cecilia O., Bailey, R., <em>Baheri, Ali</em>, Sankaran, P., and Sudit, M.</div>
  <div class="periodical"><em>Decision Analysis</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">arXiv</abbr></div>
 <div id="millard2026federated" class="col-sm-8">
  <div class="title">Federated Distributional Reinforcement Learning with Distributional Critic Regularization</div>
  <div class="author">Millard, David, Alm, Cecilia O., Ali, Rashid, Shi, Pengcheng, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>arXiv preprint</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2603.17820" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">IISE</abbr></div>
 <div id="amirishahbazi2026hospital" class="col-sm-8">
  <div class="title">Hospital and Regional Effects on Length of Stay: A Multilevel Modeling Approach</div>
  <div class="author">Amiri Shahbazi, Marzieh, <em>Baheri, Ali</em>, and Azadeh-Fard, Nasibeh</div>
  <div class="periodical"><em>IISE Transactions on Healthcare Systems Engineering</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="uq">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">AAAI</abbr></div>
 <div id="amirishahbazi2026adaptive" class="col-sm-8">
  <div class="title">Adaptive Conformal Prediction via Bayesian Uncertainty Weighting for Hierarchical Healthcare Data</div>
  <div class="author">Amiri Shahbazi, Marzieh, <em>Baheri, Ali</em>, and Azadeh-Fard, Nasibeh</div>
  <div class="periodical"><em>In SECURE-AI4H Workshop, AAAI</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2601.01223" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">L4DC</abbr></div>
 <div id="millard2026transport" class="col-sm-8">
  <div class="title">Can Optimal Transport Improve Federated Inverse Reinforcement Learning?</div>
  <div class="author">Millard, David, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Learning for Dynamics and Control Conference (L4DC)</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2601.00309" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ACC</abbr></div>
 <div id="karpoorasundarapandian2026density" class="col-sm-8">
  <div class="title">Density-Ratio Weighted Behavioral Cloning: Learning Control Policies from Corrupted Datasets</div>
  <div class="author">Karpoora Sundara Pandian, S., and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In American Control Conference (ACC)</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub highlight" data-topics="rl gen" data-award="oral">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">RLC</abbr></div>
 <div id="naghdi2026flow" class="col-sm-8">
  <div class="title">Flow-Corrected Thompson Sampling for Non-Stationary Contextual Bandits<span class="pub-award pub-award-oral" title="Oral Presentation"><i class="fas fa-microphone-alt" aria-hidden="true"></i>Oral</span></div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Continual Reinforcement Learning Workshop, RLC</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2606.23933" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ACC</abbr></div>
 <div id="baheri2026sinkhorn" class="col-sm-8">
  <div class="title">Geometry-Aware Decentralized Sinkhorn for Wasserstein Barycenters</div>
  <div class="author"><em>Baheri, Ali</em>, and Vahid, Alireza</div>
  <div class="periodical"><em>In American Control Conference (ACC)</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2509.14521" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub highlight" data-topics="uq" data-award="spotlight">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ICML</abbr></div>
 <div id="amirishahbazi2026geometry" class="col-sm-8">
  <div class="title">Geometry-Aware Uncertainty Quantification via Conformal Prediction on Manifolds<span class="pub-award pub-award-spotlight" title="Spotlight Talk"><i class="fas fa-star" aria-hidden="true"></i>Spotlight</span></div>
  <div class="author">Amiri Shahbazi, Marzieh, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Epistemic Intelligence in Machine Learning (EIML) Workshop, ICML</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2602.16015" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="gen">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ICLR</abbr></div>
 <div id="baheri2026gram" class="col-sm-8">
  <div class="title">Geometry-Grounded Flow Matching on Compact Manifolds</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Geometry-Grounded Representation Learning and Generative Modeling (GRaM) Workshop, ICLR</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub highlight" data-topics="gen" data-award="spotlight">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">NeuS</abbr></div>
 <div id="baheri2026logic" class="col-sm-8">
  <div class="title">Logic-Guided Vector Fields for Constrained Generative Modeling<span class="pub-award pub-award-spotlight" title="Spotlight Talk"><i class="fas fa-star" aria-hidden="true"></i>Spotlight</span></div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In 3rd International Conference on Neuro-Symbolic Systems (NeuS)</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2602.02009" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="gen">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ECC</abbr></div>
 <div id="baheri2026metriplectic" class="col-sm-8">
  <div class="title">Metriplectic Conditional Flow Matching for Structure-Preserving Dynamics Learning</div>
  <div class="author"><em>Baheri, Ali</em>, and Lindemann, Lars</div>
  <div class="periodical"><em>In European Control Conference (ECC)</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">CDC</abbr></div>
 <div id="baheri2026wasserstein" class="col-sm-8">
  <div class="title">Wasserstein Stability of Contracting Flows: Effective Rates, Euler Self-Correction, and Noise Tightening</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In IEEE Conference on Decision and Control (CDC)</em> 2026</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2607.14291" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ICLR</abbr></div>
 <div id="baheri2026pde" class="col-sm-8">
  <div class="title">What Does a Neural PDE Solver Really Learn? A Residual-Spectrum Diagnostic</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In AI and Partial Differential Equations Workshop, ICLR</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub highlight" data-topics="ot rl" data-award="oral">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">AAAI</abbr></div>
 <div id="salgarkar2026distance" class="col-sm-8">
  <div class="title">When Distance Matters: Wasserstein Trust Regions for Multi-Agent Coordination<span class="pub-award pub-award-oral" title="Oral Presentation"><i class="fas fa-microphone-alt" aria-hidden="true"></i>Oral</span></div>
  <div class="author">Salgarkar, Chirayu, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Multi-Agent Path Finding Workshop, AAAI</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="gen">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">CCS</abbr></div>
 <div id="baheri2026debate" class="col-sm-8">
  <div class="title">When Does Multi-Agent Language-Model Debate Converge? A Bifurcation on the Probability Simplex</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Conference on Complex Systems (CCS)</em> 2026</div>
  <div class="links"></div>
 </div>
</div>
</li>
</ol>
</div>
<div class="year-group" data-year="2025">
<h2 class="year">2025</h2>
<ol class="bibliography">
<li class="pub" data-topics="uq">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">RAM</abbr></div>
 <div id="baheri2025conformal" class="col-sm-8">
  <div class="title">Conformal Prediction Across Scales: Finite-Sample Coverage with Hierarchical Efficiency</div>
  <div class="author"><em>Baheri, Ali</em>, and Amiri Shahbazi, Marzieh</div>
  <div class="periodical"><em>Results in Applied Mathematics</em> 2025</div>
  <div class="links">
 <a href="https://www.sciencedirect.com/science/article/pii/S2590037425000536" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="uq">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">RICO</abbr></div>
 <div id="baheri2025lyapunov" class="col-sm-8">
  <div class="title">Distributionally Robust Lyapunov-Barrier Networks for Safe and Stable Control Under Uncertainty</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>Results in Control and Optimization</em> 2025</div>
  <div class="links">
 <a href="https://www.sciencedirect.com/science/article/pii/S2666720725000426" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">Logics</abbr></div>
 <div id="baheri2025temporal" class="col-sm-8">
  <div class="title">Multi-Fidelity Temporal Reasoning: A Stratified Logic for Cross-Scale System Specifications</div>
  <div class="author"><em>Baheri, Ali</em>, and Wei, Peng</div>
  <div class="periodical"><em>Logics</em> 2025</div>
  <div class="links">
 <a href="https://www.mdpi.com/2813-0405/3/2/5" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">MDPI</abbr></div>
 <div id="baheri2025multilevel" class="col-sm-8">
  <div class="title">Multilevel Constrained Bandits: A Hierarchical Upper Confidence Bound Approach with Safety Guarantees</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>Mathematics</em> 2025</div>
  <div class="links">
 <a href="https://www.mdpi.com/2227-7390/13/1/149" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">NeurIPS</abbr></div>
 <div id="baheri2025backdoor" class="col-sm-8">
  <div class="title">Geometry-Aware Backdoor Attacks: Leveraging Curvature in Hyperbolic Embeddings</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Non-Euclidean Foundation Models and Geometric Learning Workshop, NeurIPS</em> 2025</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2510.06397" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl gen">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">NeSy</abbr></div>
 <div id="baheri2025neurosymbolic" class="col-sm-8">
  <div class="title">Hierarchical Neuro-Symbolic Decision Transformer</div>
  <div class="author"><em>Baheri, Ali</em>, and Alm, Cecilia O.</div>
  <div class="periodical"><em>In 19th International Conference on Neurosymbolic Learning and Reasoning (NeSy)</em> 2025</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2503.07148" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 <a href="https://openreview.net/forum?id=tXOU6EULup" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">RSS</abbr></div>
 <div id="baheri2025implicit" class="col-sm-8">
  <div class="title">Implicit Constraint-Aware Off-Policy Correction for Offline Reinforcement Learning</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Out-of-Distribution Generalization in Robotics Workshop, RSS</em> 2025</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2506.14058" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="gen">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">NeurIPS</abbr></div>
 <div id="baheri2025metriplectic" class="col-sm-8">
  <div class="title">Metriplectic Conditional Flow Matching for Dissipative Dynamics</div>
  <div class="author"><em>Baheri, Ali</em>, and Lindemann, Lars</div>
  <div class="periodical"><em>In Dynamics at the Frontiers of Optimization, Sampling, and Games (DynaFront) Workshop, NeurIPS</em> 2025</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2509.19526" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">L4DC</abbr></div>
 <div id="baheri2025wave" class="col-sm-8">
  <div class="title">WAVE: Wasserstein Adaptive Value Estimation for Actor-Critic Reinforcement Learning</div>
  <div class="author"><em>Baheri, Ali</em>, Shahrooei, Zahra, and Salgarkar, Chirayu</div>
  <div class="periodical"><em>In Learning for Dynamics and Control Conference (L4DC)</em> 2025</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ICML</abbr></div>
 <div id="baheri2025barycenter" class="col-sm-8">
  <div class="title">Wasserstein-Barycenter Consensus for Cooperative Multi-Agent Reinforcement Learning</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Multi-Agent Systems in the Era of Foundation Models Workshop, ICML</em> 2025</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2506.12497" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
</ol>
</div>
<div class="year-group" data-year="2024">
<h2 class="year">2024</h2>
<ol class="bibliography">
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">EAAI</abbr></div>
 <div id="razzaghi2024survey" class="col-sm-8">
  <div class="title">A Survey on Reinforcement Learning in Aviation Applications</div>
  <div class="author">Razzaghi, Pouria, Tabrizian, Amin, Guo, Wei, Chen, Shulu, Taye, Abenezer, Thompson, Ellis, Bregeon, Alexis, <em>Baheri, Ali</em>, and Wei, Peng</div>
  <div class="periodical"><em>Engineering Applications of Artificial Intelligence</em> 2024</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2211.02147" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 <a href="https://www.sciencedirect.com/science/article/abs/pii/S0952197624010698" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">IEEE Access</abbr></div>
 <div id="yancosek2024beacon" class="col-sm-8">
  <div class="title">BEACON: A Bayesian Evolutionary Approach for Counterexample Generation of Control Systems</div>
  <div class="author">Yancosek, J., and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>IEEE Access</em> 2024</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2403.05925" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 <a href="https://ieeexplore.ieee.org/document/10620179" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">OJ-CSYS</abbr></div>
 <div id="yifru2024concurrent" class="col-sm-8">
  <div class="title">Concurrent Learning of Control Policy and Unknown Safety Specifications in Reinforcement Learning</div>
  <div class="author">Yifru, L., and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>IEEE Open Journal of Control Systems</em> 2024</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2402.15893" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 <a href="https://ieeexplore.ieee.org/abstract/document/10569078" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">PLOS ONE</abbr></div>
 <div id="hayes2024forward" class="col-sm-8">
  <div class="title">Forward Variable Selection Enables Fast and Accurate Dynamic System Identification with Karhunen-Loève Decomposed Gaussian Processes</div>
  <div class="author">Hayes, K., Fouts, M., <em>Baheri, Ali</em>, and Mebane, D.</div>
  <div class="periodical"><em>PLOS ONE</em> 2024</div>
  <div class="links">
 <a href="https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0309661" class="btn btn-sm z-depth-0" role="button" target="_blank">HTML</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">arXiv</abbr></div>
 <div id="baheri2024synergy" class="col-sm-8">
  <div class="title">The Synergy Between Optimal Transport Theory and Multi-Agent Reinforcement Learning</div>
  <div class="author"><em>Baheri, Ali</em>, and <a href="https://scholar.google.com/citations?user=cAy9G6oAAAAJ" target="_blank">Kochenderfer, Mykel J.</a></div>
  <div class="periodical"><em>arXiv preprint</em> 2024</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2401.10949" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">RSS</abbr></div>
 <div id="shahrooei2024transport" class="col-sm-8">
  <div class="title">Optimal Transport-Assisted Risk-Sensitive Q-Learning</div>
  <div class="author">Shahrooei, Zahra, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Towards Safe Autonomy: Emerging Requirements, Definitions, and Methods Workshop, RSS</em> 2024</div>
  <div class="links"></div>
 </div>
</div>
</li>
</ol>
</div>
<div class="year-group" data-year="2023">
<h2 class="year">2023</h2>
<ol class="bibliography">
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">AI Mag.</abbr></div>
 <div id="baheri2023fidelity" class="col-sm-8">
  <div class="title">Exploring the Role of Simulator Fidelity in the Safety Validation of Learning-Enabled Autonomous Systems</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>AI Magazine</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">arXiv</abbr></div>
 <div id="baheri2023fidelitysettings" class="col-sm-8">
  <div class="title">Joint Falsification and Fidelity Settings Optimization for Validation of Safety-Critical Systems: A Theoretical Analysis</div>
  <div class="author"><em>Baheri, Ali</em>, and <a href="https://scholar.google.com/citations?user=cAy9G6oAAAAJ" target="_blank">Kochenderfer, Mykel J.</a></div>
  <div class="periodical"><em>arXiv preprint</em> 2023</div>
  <div class="links">
 <a href="https://arxiv.org/abs/2305.06111" class="btn btn-sm z-depth-0" role="button" target="_blank">arXiv</a>
 </div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ECC</abbr></div>
 <div id="shahrooei2023falsification" class="col-sm-8">
  <div class="title">Falsification of Learning-Based Controllers through Multi-Fidelity Bayesian Optimization</div>
  <div class="author">Shahrooei, Zahra, <a href="https://scholar.google.com/citations?user=cAy9G6oAAAAJ" target="_blank">Kochenderfer, Mykel J.</a>, and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In European Control Conference (ECC)</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ICAPS</abbr></div>
 <div id="yifru2023joint" class="col-sm-8">
  <div class="title">Joint Learning of Policy with Unknown Temporal Constraints for Safe Reinforcement Learning</div>
  <div class="author">Yifru, L., and <em>Baheri, Ali</em></div>
  <div class="periodical"><em>In PRL Workshop Series: Bridging the Gap Between AI Planning and Reinforcement Learning, ICAPS</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="gen rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">NeurIPS</abbr></div>
 <div id="baheri2023llms" class="col-sm-8">
  <div class="title">LLMs-Augmented Contextual Bandit</div>
  <div class="author"><em>Baheri, Ali</em>, and Alm, Cecilia O.</div>
  <div class="periodical"><em>In Foundation Models for Decision Making Workshop, NeurIPS</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">ICAPS</abbr></div>
 <div id="baheri2023policy" class="col-sm-8">
  <div class="title">Policy Refinement with Human Feedback for Safe Reinforcement Learning</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In PRL Workshop Series: Bridging the Gap Between AI Planning and Reinforcement Learning, ICAPS</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">IROS</abbr></div>
 <div id="baheri2023risk" class="col-sm-8">
  <div class="title">Risk-Aware Reinforcement Learning Through Optimal Transport Theory</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In 3rd RL-CONFORM Workshop, IROS</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">AAAI</abbr></div>
 <div id="baheri2023validation" class="col-sm-8">
  <div class="title">Safety Validation of Learning-Based Autonomous Systems: A Multi-Fidelity Approach</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Proceedings of the AAAI Conference on Artificial Intelligence (New Faculty Highlights)</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
<li class="pub" data-topics="ot rl">
<div class="row">
 <div class="col-sm-2 abbr"><abbr class="badge">NeurIPS</abbr></div>
 <div id="baheri2023reward" class="col-sm-8">
  <div class="title">Understanding Reward Ambiguity Through Optimal Transport Theory in Inverse Reinforcement Learning</div>
  <div class="author"><em>Baheri, Ali</em></div>
  <div class="periodical"><em>In Optimal Transport and Machine Learning Workshop, NeurIPS</em> 2023</div>
  <div class="links"></div>
 </div>
</div>
</li>
</ol>
</div>

</div>

<div class="pub-count" id="pub-count"></div>

<script>
(function () {
  var search = document.getElementById('pub-search');
  var chips = document.querySelectorAll('#pub-chips button');
  var pubs = document.querySelectorAll('.publications li.pub');
  var groups = document.querySelectorAll('.publications .year-group');
  var counter = document.getElementById('pub-count');
  var topic = 'all';

  function apply() {
    var term = search.value.trim().toLowerCase();
    var shown = 0;
    pubs.forEach(function (p) {
      var okTopic;
      if (topic === 'all') {
        okTopic = true;
      } else if (topic === 'award') {
        okTopic = p.classList.contains('highlight');
      } else {
        okTopic = (p.getAttribute('data-topics') || '').split(' ').indexOf(topic) > -1;
      }
      var okTerm = term === '' || p.textContent.toLowerCase().indexOf(term) > -1;
      var visible = okTopic && okTerm;
      p.style.display = visible ? '' : 'none';
      if (visible) shown++;
    });
    groups.forEach(function (g) {
      var any = false;
      g.querySelectorAll('li.pub').forEach(function (p) {
        if (p.style.display !== 'none') { any = true; }
      });
      g.style.display = any ? '' : 'none';
    });
    counter.textContent = 'Showing ' + shown + ' of ' + pubs.length + ' publications';
  }

  chips.forEach(function (c) {
    c.addEventListener('click', function () {
      topic = c.getAttribute('data-topic');
      chips.forEach(function (x) { x.classList.remove('active'); });
      c.classList.add('active');
      apply();
    });
  });
  search.addEventListener('input', apply);
  apply();
})();
</script>
