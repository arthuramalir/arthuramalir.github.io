---
layout: post
title:  "0D Lumped-Parameter Cardiovascular Model"
date:   2026-05-22 03:00:00 -0500
---

<div style="font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, 'Liberation Mono', 'Courier New', monospace; font-size: 0.9rem; line-height: 1.7; color: #e0e0e0; letter-spacing: -0.01em;">

A multi-chamber lumped-parameter model of the human cardiovascular system that captures the complex dynamics of blood flow, pressure, and valve mechanics through a system of coupled ODEs.

## Model Overview

The 0D model represents the cardiovascular system as a network of compliant chambers (left/right atria and ventricles), peripheral resistances, and compliance elements. Each chamber is governed by:

**Pressure-Volume Relationship:**
- Time-varying elastance: E(t) = E_min + (E_max - E_min) * activation(t)
- Pressure: P = E(t) * (V - V_d) + P_0

**Key Features:**
- Realistic valve dynamics (tricuspid, mitral, aortic, pulmonary)
- Systemic and pulmonary circulation loops
- Baroreceptor feedback mechanisms
- Parameter estimation from clinical data

## Applications

This model is valuable for:
- Understanding pathophysiological conditions (heart failure, hypertension)
- Drug efficacy testing in computational frameworks
- Patient-specific cardiovascular analysis
- Teaching cardiovascular physiology

The model demonstrates the power of reduced-order modeling in capturing complex physiological systems with computational efficiency.

</div>
