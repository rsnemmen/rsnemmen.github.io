---
layout: page
title: GPUmonty
description: GPU-accelerated Monte Carlo radiative transfer for black hole spectra
img: assets/img/gpumonty-vs-igrmonty.png
importance: 1
category: astrophysics
github: https://github.com/black-hole-group/gpumonty
---

<div class="alert alert-info"><h4>Executive Summary</h4><p>
GPUmonty is a CUDA/C GPU-accelerated relativistic Monte Carlo radiative transfer code for simulating spectra from accreting black holes. This is a group effort developed with Pedro Motta and collaborators. It follows photon packets, or superphotons, through curved spacetime around black holes and models synchrotron emission, geodesic propagation, Compton scattering, and spectra seen from different viewing angles.
</p></div>

GPUmonty was built to make black hole spectral modeling faster. The project grew from joint work with Pedro Motta and the black hole group, and is based on the Monte Carlo methods used in `grmonty` and `igrmonty`. It moves the most expensive photon generation, tracking, and scattering calculations onto NVIDIA GPUs. In benchmark tests, this gives roughly an order-of-magnitude speedup compared with CPU-based workflows while preserving the physics needed for multiwavelength spectra.

## Why it matters

Synthetic spectra are essential for connecting general relativistic magnetohydrodynamic simulations to observations of active galactic nuclei, X-ray binaries, and horizon-scale sources such as M87* and Sgr A*. But Monte Carlo radiative transfer is expensive, which limits how many models, observer inclinations, electron-heating prescriptions, and black hole parameters can be explored.

GPUmonty reduces that bottleneck. Faster spectra make it more practical to run large parameter surveys, compare accretion models against multiwavelength data, and build forward-modeling pipelines for interpreting black hole observations.

## What the code does

- Traces superphotons through the Kerr spacetime around a black hole
- Computes thermal synchrotron emission from hot electrons
- Models Compton scattering in Thomson and Klein-Nishina regimes
- Produces spectra binned by observer viewing angle
- Reads GRMHD simulation data, including `iharm3D` HDF5 dumps
- Uses CUDA C++ for GPU kernels, C/OpenMP for host-side work, and Python for post-processing

## Resources

- [Introductory blog post](https://nemmen.bearblog.dev/introducing-gpumonty-simulating-black-hole-light-with-gpus/)
- [GitHub repository](https://github.com/black-hole-group/gpumonty)
- [Documentation](https://black-hole-group.github.io/gpumonty/)
- [Paper: GPUmonty: GPU-accelerated relativistic Monte Carlo radiative transfer code](https://arxiv.org/abs/2602.13198)
