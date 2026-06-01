---
layout: page
title: Projects
permalink: /projects/
---

This page summarizes selected quantitative and scientific-computing projects. Code repositories and technical details are available on GitHub: [github.com/arthuramalir](https://github.com/arthuramalir)

---

## Computational Modeling & Simulation

### Multiscale Diffusion in Random Networks (Columbia) — Monte Carlo & Stochastic Methods

Built a scalable Monte Carlo PDE solver for random 3D Voronoi networks—demonstrating practical techniques for modeling uncertainty and stochastic phenomena at scale.

**Skills:** Monte Carlo Methods • Stochastic Systems • Uncertainty Quantification • Numerical Analysis  
**Impact:** Discovered power-law scaling behavior ($L_{REV} \propto \rho^{-1/2}$), enabling efficient computation across scales

**Highlights:**
- Implemented simulation workflows for stochastic network geometries
- Investigated convergence behavior and representative volume element effects
- Observed scaling consistent with connected path structures
- **Methods Demonstrated:** Monte Carlo sampling, variance analysis, large-scale computational simulation

**Deep Dive:** Read the blog post [Curse of Dimensionality in Multiscale Diffusion]({{ '/2026/06/01/curse-of-dimensionality-multiscale-diffusion.html' | relative_url }})

**Academic Paper:**
<embed src="/assets/NA4PDEs_project.pdf" type="application/pdf" width="100%" height="500px" />

---

### Smectite-Clay Transport Modeling (ESTP / Ecole des Ponts / ADEME) — Data Integration & Model Calibration

Developed C++ and FreeFEM++ computational models and integrated multi-source experimental/simulation datasets for parameter estimation and model validation.

**Skills:** Model Calibration • Data Integration • FreeFEM++ • C++  
**Impact:** Identified electrostatic interactions as dominant rate-limiting transport mechanism

**Highlights:**
- Built and validated high-fidelity computational models against experimental data
- Performed rigorous data cleaning, validation, and integration across multiple data sources
- Identified dominant physical mechanisms through model-driven analysis
- Contributed to research direction in the IRGAK project
- **Methods Demonstrated:** Model calibration, multi-source data integration, sensitivity analysis, validation against experimental baselines

---

### Tsunami Wave Propagation Modeling (ESTP) — Large-Scale Optimization & Numerical Methods

Optimized large-scale MATLAB numerical models for wave propagation and barrier effectiveness—achieving 100x speedup through algorithmic improvements.

**Skills:** Numerical Optimization • MATLAB • Performance Profiling • Physics-Based Simulation  
**Impact:** 100x computational speedup, validated wave run-up reduction (40%)

**Highlights:**
- Reduced runtime by ~100x through code optimization and numerical method refinement
- Captured physical phenomena (40% wave run-up reduction from natural barriers) with validated models
- Validated computational results against experimental data
- **Methods Demonstrated:** Numerical optimization, performance profiling, large-scale simulation, result validation

---

### Automatic Cough Recognition Using ML (Lycee Janson de Sailly) — Time Series & Machine Learning

Built an end-to-end Python machine learning pipeline for audio signal classification using time-frequency feature extraction.

**Skills:** Python • Signal Processing • Machine Learning • Feature Engineering  
**Impact:** 91% validation accuracy on real-world noisy data

**Highlights:**
- Implemented preprocessing, mel-spectrogram feature extraction, and classification pipeline
- Achieved 91% validation accuracy on noisy real-world audio data
- **Methods Demonstrated:** Time series feature engineering, noise handling, model training and validation, real-world data challenges

---

### Numerical Methods for PDEs (Columbia) — Advanced Computational Mathematics

Advanced coursework and projects in numerical methods for solving partial differential equations—studying convergence, stability, and implementation of modern computational techniques.

**Skills:** Numerical Analysis • PDE Theory • Computational Methods • Mathematical Modeling

**Highlights:**
- Convergence analysis and stability testing of discretization schemes
- Implementation of modern numerical methods for diverse PDE classes
- Theoretical and practical investigation of stability-accuracy tradeoffs

**Academic Paper:**
<embed src="/assets/ENME_6220_project.pdf" type="application/pdf" width="100%" height="500px" />

---

## Interactive Projects

### [Game of Life]({{ '/game-of-life/' | relative_url }})

An interactive implementation of Conway's Game of Life—demonstrating how complex emergent behavior arises from simple rules. A fun analogy to computational modeling: starting with basic equations, watching sophisticated dynamics unfold.

**Skills:** Web Development • JavaScript • Algorithm Design • Cellular Automata

---

More projects and case studies will be added as I complete additional work in computational science and applied mathematics.
