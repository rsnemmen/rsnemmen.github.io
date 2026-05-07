---
layout: page
title: MHD Simulation Analysis Toolkit
description: Python toolkit for post-processing, diagnostics, and visualization of PLUTO MHD simulations
img: assets/img/mickey/image.png
importance: 2
category: astrophysics
github: https://github.com/black-hole-group/mickey
---

<div class="alert alert-info"><h4>Executive Summary</h4><p>
This project is a Python analysis package for magnetohydrodynamic simulation workflows. I developed and maintained it to support team-wide post-processing, diagnostic parsing, coordinate transformations, and visualization of PLUTO simulation outputs. The package turned repeated analysis tasks into reusable tools for reading dumps, computing physical diagnostics, and producing publication-ready views of accretion-flow simulations.
</p></div>

Large MHD simulation campaigns produce many output files, derived quantities, and diagnostic plots. This toolkit was built to make that workflow less manual: simulation data could be loaded through `pyPLUTO`, converted into convenient analysis objects, and passed through shared routines for plotting, regridding, and measuring accretion-flow properties.

<div class="row">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/mickey/image.png" title="PLUTO MHD simulation visualization" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
<div class="caption">
Example visualization of a PLUTO simulation output produced with the analysis workflow.
</div>

## Why it matters

Astrophysical MHD simulations are essential for studying accretion flows, jets, and magnetized plasma dynamics, but the raw outputs are not immediately useful for scientific interpretation. Researchers need reproducible ways to parse simulation dumps, compute derived quantities, compare snapshots, and visualize scalar and vector fields.

By collecting those operations into a shared Python package, this project reduced repeated notebook-level code and made analysis workflows easier to reuse across simulations and collaborators.

## What the code does

- Reads PLUTO binary output through `pyPLUTO`
- Stores simulation variables, grids, velocities, pressure, density, and metadata in reusable Python objects
- Computes diagnostics such as mass, accretion rates, Bernoulli function, angular momentum, sound speed, and Mach number
- Supports density maps, mesh plots, streamlines, and other visual diagnostics
- Performs coordinate transformations and regridding between spherical and Cartesian views
- Includes optional C, SWIG, OpenMP, OpenACC, and GPU-accelerated paths for expensive array operations

## Technical approach

The central interface wraps a PLUTO output frame in a Python object with grid coordinates, fluid variables, derived fields, and simulation metadata attached as attributes. Analysis routines can then operate on this common representation instead of repeatedly handling low-level dump parsing.

The plotting layer focuses on common MHD inspection tasks such as density maps, computational meshes, and cropped streamplots. For expensive coordinate transformations, the project includes compiled acceleration paths so large simulation arrays can be regridded much faster than with pure Python loops.

## Resources

- [GitHub repository](https://github.com/black-hole-group/mickey)
