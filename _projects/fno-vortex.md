---
layout: page
title: Fourier Neural Operator for Magnetized Plasmas
description: Neural operator surrogate for 2D MHD turbulence simulations
img: assets/video/magfield.webp
importance: 1
category: ai
github: https://github.com/black-hole-group/fno-vortex/tree/dev
---

<div class="alert alert-info"><h4>Executive Summary</h4><p>
This project implements a PyTorch Fourier Neural Operator surrogate for magnetized plasma simulations. The current development branch trains 3D FNO models on Idefix simulations of the Orszag-Tang vortex, a canonical benchmark for compressible magnetohydrodynamic turbulence. Given a short window of simulation frames plus physical parameters, the model predicts the future evolution of density, velocity, and magnetic-field components on a 128x128 grid.
</p></div>

Neural operator surrogates are useful when physics simulations are accurate but expensive. In this project, the FNO learns a mapping from initial plasma states and transport coefficients to future MHD states, making it possible to explore simulation behavior faster than running a full numerical solver for every parameter choice.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/video/magfield.webp" title="FNO prediction for magnetized plasma dynamics" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
Comparison between ground-truth simulated magnetic-field structure, the FNO prediction, and residuals for an MHD vortex.
</div>

## Why it matters

Magnetohydrodynamic simulations describe conducting fluids coupled to magnetic fields. They are central to astrophysical plasma problems such as accretion flows, jets, stellar atmospheres, and the interstellar medium, but parameter sweeps over viscosity and magnetic diffusivity quickly become expensive.

The Orszag-Tang vortex is a demanding benchmark because smooth initial conditions rapidly develop shocks, interacting vortices, and turbulent magnetic structures. A surrogate that can generalize across transport parameters is therefore learning more than a static image-to-image mapping; it is approximating the time-evolution operator of the underlying PDE system.

## What the code does

- Trains a 3D Fourier Neural Operator on 2D Idefix MHD simulations
- Predicts density, velocity components, and magnetic-field components
- Conditions predictions on kinematic viscosity and Ohmic diffusivity
- Uses 128x128 spatial grids with temporal windows of simulation frames
- Supports training, inference, dense reference preparation, and scalar/vector visualization
- Runs autoregressive rollout, feeding predicted frames back as inputs for longer forecasts

## Technical approach

The model receives a short sequence of field snapshots together with the physical parameters for the simulation. Spatial and temporal coordinates are appended internally, then the tensor is lifted into a higher-dimensional representation and processed by Fourier layers. Each layer combines spectral convolution in the frequency domain with a local skip path, allowing the network to capture both long-range structure and local features.

The current `dev` workflow uses Idefix-generated Orszag-Tang data rather than the older FARGO3D training path described in the original paper-era implementation. The dataset uses independent viscosity and diffusivity values, explicit train/validation/test splits, and held-out test cases reserved for final inference.

## Current status

The repository contains working scripts for model training, inference, reference preparation, and visual diagnostics. The current supported path is the Idefix workflow on the `dev` branch. Older FARGO3D assets remain as historical context, but the development focus has moved to a cleaner data pipeline, validation-based model selection, and autoregressive forecasting.

## Resources

- [Introductory blog post](https://nemmen.bearblog.dev/neural-operator-surrogate-for-magnetized-plasma-simulations/)
- [GitHub repository, dev branch](https://github.com/black-hole-group/fno-vortex/tree/dev)
- [Paper: Spectral Learning of Magnetized Plasma Dynamics: A Neural Operator Application](https://arxiv.org/abs/2507.01388)
