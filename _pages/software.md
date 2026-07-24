---
layout: page
permalink: /software/
title: software
description: We build open-source tools that turn our research into software others can use. Our work lives on the <a href="https://github.com/SAILRIT" target="_blank">Safe AI Lab GitHub</a>.
nav: true
nav_order: 4
---

<!-- Plain HTML on purpose: no Jekyll plugins required, so this builds on
     GitHub Pages with no extra setup. -->

<style>
.sw-hero {
  border: 1px solid color-mix(in srgb, var(--global-text-color) 14%, transparent);
  border-radius: 12px; padding: 1.6rem 1.5rem; margin-bottom: 1.6rem;
  background: linear-gradient(135deg,
    color-mix(in srgb, var(--global-theme-color) 8%, transparent),
    color-mix(in srgb, var(--global-theme-color) 2%, transparent));
}
.sw-hero .eyebrow {
  font-size: .72rem; text-transform: uppercase; letter-spacing: .1em;
  font-weight: 700; color: var(--global-theme-color);
}
.sw-hero h2 {
  margin: .35rem 0 .1rem; font-size: 1.7rem; font-family: monospace; letter-spacing: -.5px;
}
.sw-hero .tagline { font-size: 1.02rem; line-height: 1.6; margin-top: .55rem; }
.sw-badges { display: flex; flex-wrap: wrap; gap: .45rem; margin-top: 1rem; }
.sw-badges span {
  font-size: .72rem; font-weight: 600; padding: .2rem .7rem; border-radius: 999px;
  background: color-mix(in srgb, var(--global-theme-color) 14%, transparent);
  color: color-mix(in srgb, var(--global-theme-color) 82%, var(--global-text-color));
}
.sw-cta {
  display: inline-flex; align-items: center; gap: .5rem; margin-top: 1.2rem;
  padding: .5rem 1.1rem; border-radius: 6px; font-size: .9rem; font-weight: 600;
  color: #fff !important; text-decoration: none !important;
  background: var(--global-theme-color);
  background: linear-gradient(135deg, var(--global-theme-color),
    color-mix(in srgb, var(--global-theme-color) 60%, #000));
  transition: transform .18s ease, box-shadow .18s ease;
}
.sw-cta:hover { transform: translateY(-2px);
  box-shadow: 0 6px 16px color-mix(in srgb, var(--global-theme-color) 34%, transparent); }

.sw-methods { list-style: none; padding: 0; margin: 1.4rem 0; }
.sw-methods li {
  display: flex; gap: .9rem; align-items: baseline;
  padding: .7rem .8rem; border-radius: 6px;
  border-left: 3px solid var(--global-theme-color); margin-bottom: .55rem;
  background: color-mix(in srgb, var(--global-theme-color) 4%, transparent);
}
.sw-methods code {
  flex: 0 0 auto; font-weight: 700; color: var(--global-theme-color);
  background: none; padding: 0;
}
.sw-methods .m-desc { font-size: .9rem; line-height: 1.5; }
.sw-methods .m-ref { color: var(--global-text-color-light); font-size: .82rem; }

.sw-snippet {
  background: var(--global-code-bg-color); border-radius: 8px;
  padding: 1rem 1.1rem; overflow-x: auto; font-size: .82rem; line-height: 1.55;
  margin: 1.2rem 0;
}
.sw-more {
  margin-top: 2.4rem; padding: 1.2rem 1.3rem; border-radius: 10px;
  border: 1px dashed color-mix(in srgb, var(--global-text-color) 22%, transparent);
}
.sw-more h3 { margin-top: 0; font-size: 1.05rem; }

@media (prefers-reduced-motion: reduce) { .sw-cta:hover { transform: none; } }
</style>

<div class="sw-hero" markdown="1">
<div class="eyebrow">Featured &middot; Julia package</div>
<h2>NeuralOT.jl</h2>
<div class="tagline">Neural optimal transport in Julia — estimate Monge maps, dual potentials, and transport-based generative models with neural networks.</div>
<div class="sw-badges">
<span>Julia</span><span>MIT licensed</span><span>Optimal transport</span><span>Generative modeling</span>
</div>
<a class="sw-cta" href="https://github.com/SAILRIT/NeuralOT.jl" target="_blank">View on GitHub &rarr;</a>
</div>

Optimal transport is a thread that runs through much of our research, but the Julia
ecosystem had a gap. Packages such as **OptimalTransport.jl** solve the discrete,
entropic problem well — Sinkhorn iterations and exact linear programs over weighted
point clouds. What was missing was *neural* optimal transport: the continuous methods
that scale to high dimensions by parameterising the potential or the transport map as
a neural network, and that generalise beyond the training samples. **NeuralOT.jl**
fills that gap.

The package implements three established families of methods behind a single, consistent
interface:

<ul class="sw-methods">
<li><code>solve_dual</code><span class="m-desc">Entropic OT in high dimensions directly from samples, when you need the cost or the dual potentials.<br><span class="m-ref">Seguy et al., ICLR 2018</span></span></li>
<li><code>solve_w2</code><span class="m-desc">Wasserstein-2 Monge maps via input-convex neural networks, when you need a valid transport map with provable convexity structure.<br><span class="m-ref">Makkuva et al., ICML 2020</span></span></li>
<li><code>flow_match</code><span class="m-desc">Transport-based generative models that move noise to data, with simulation-free training that scales to large datasets.<br><span class="m-ref">Lipman et al., ICLR 2023</span></span></li>
</ul>

The common interface means switching methods is a one-line change. Learn a squared-cost
Monge map between two distributions, then push samples through it:

<div class="sw-snippet" markdown="0">
<pre style="margin:0;background:none;"><code>result = solve_w2(sample_&mu;, sample_&nu;; dim=2, steps=2_000)
T_X    = monge_map(result, X)   # transported samples</code></pre>
</div>

Worked examples, installation instructions, and the method-selection guide are in the
repository. The package is MIT licensed and open to contributions.

<div class="sw-more" markdown="1">
### More from the Safe AI Lab

NeuralOT.jl is one of several open-source releases from our group. Others accompany
individual papers — implementations of multi-fidelity Bayesian optimization for
falsification, risk-averse temporal-difference learning, and concurrent learning of
control policies under unknown constraints, among others. All of it lives on the
[Safe AI Lab GitHub organization](https://github.com/SAILRIT){:target="_blank"}.
</div>
