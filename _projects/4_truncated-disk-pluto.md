---
layout: page
title: Truncated Disk Simulations
description: Hot coronae and truncated thin disks in simulations of accreting stellar-mass black holes
img: assets/img/truncated-disk-pluto/money-plot.jpg
importance: 1
category: astrophysics
---

<div class="alert alert-info"><h4>Executive Summary</h4><p>
This project studies how a cold, truncated thin disk and a hot X-ray-emitting corona can emerge naturally in simulations of accreting stellar-mass black holes. We used two-dimensional hydrodynamical simulations with radiative cooling to model accretion flows in X-ray binaries, varying the mass accretion rate across the range relevant for hard-state systems. The simulations show that as the accretion rate increases, the corona contracts and the inner edge of the thin disk moves closer to the black hole.
</p></div>

Black hole X-ray binaries cycle between hard and soft spectral states. In the hard state, observations are commonly interpreted with a geometry in which a hot corona coexists with a colder thin disk whose inner edge is truncated away from the event horizon. The physics that forms the corona, sets the truncation radius, and drives the hard-to-soft transition is still debated.

This work addresses that problem with numerical simulations designed to follow the collapse of a hot accretion flow when radiative cooling becomes dynamically important.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/truncated-disk-pluto/money-plot.jpg" title="Temperature and density maps from truncated disk simulations" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
Temperature and density maps from five simulations with different accretion rates. The left side of each panel shows electron temperature, while the right side shows electron number density.
</div>

## Scientific Motivation

In X-ray binaries, the hard state is associated with a hard power-law X-ray spectrum and is usually modeled with a hot corona or radiatively inefficient accretion flow inside a truncated thin disk. As the source brightens, the thin disk is expected to move inward and the system transitions toward the soft state.

The central questions are:

- How does a hot corona form and survive around a stellar-mass black hole?
- What controls the inner radius of the thin disk?
- Does the disk truncation radius decrease as the accretion rate increases?

## Numerical Experiment

We performed two-dimensional hydrodynamical simulations of accretion onto a $10 M_\odot$ black hole using the PLUTO code. The simulations approximate Schwarzschild gravity with a pseudo-Newtonian potential and include radiative losses from bremsstrahlung, synchrotron emission, synchrotron self-Compton cooling, and optically thick cooling in dense regions.

The initial condition is a hot torus. After a burn-in phase, radiative cooling is enabled and the flow is allowed to evolve. We varied the accretion rate over $0.02 \leq \dot{M}/\dot{M}_{\rm Edd} \leq 0.35$, covering the regime where hard-state X-ray binaries are expected to transition between radiatively inefficient and thin-disk-dominated accretion.

## Main Results

For $\dot{M}/\dot{M}_{\rm Edd} \geq 0.06$, the simulations form a cold thin disk embedded inside a hot corona. The disk is dense and geometrically thin, while the corona remains hot, with typical electron temperatures of $10^{9}$-$10^{10}$ K.

At the lowest simulated accretion rate, $\dot{M}/\dot{M}_{\rm Edd} = 0.02$, the thin disk disappears and the flow remains hot and geometrically thick. This constrains the critical accretion rate for the disk to disappear to roughly $0.02 < \dot{M}_{\rm crit}/\dot{M}_{\rm Edd} \lesssim 0.06$.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="lazy" path="assets/img/truncated-disk-pluto/corona.png" title="Corona height and thin disk inner radius versus accretion rate" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
The corona height and thin disk inner radius both decrease as the accretion rate increases.
</div>

The trends are consistent with the standard picture of state transitions: increasing accretion rate leads to stronger cooling, a smaller corona, and a thin disk whose inner edge approaches the black hole.

## Observational Relevance

The simulations provide a physical mechanism for the hard-state geometry inferred in X-ray binaries. They predict that the disk inner radius should anticorrelate with accretion rate and luminosity, matching the qualitative behavior expected from observations of systems such as GX 339-4.

The work also suggests that a compact corona can persist even at luminosities typical of softer states, potentially contributing to the hard X-ray tail observed in some systems.
