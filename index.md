---
layout: home
title: Andrew Fan
---

# Andrew Fan

EE undergrad at UCLA. I work on computer architecture, RTL design, and ML systems — mostly making inference go fast on small hardware.

[email](mailto:andrewkongfan@gmail.com) · [github](https://github.com/im-afan)

## Projects

**[Int4 Transformer & Custom TPU-Style Accelerator](/transformer-tpu/)** — Summer 2026 – present

A decoder-only transformer written from scratch in PyTorch (ReLU attention, int4 weights and activations, dynamic-tanh norm) running end to end on a TPU-style accelerator I built in SystemVerilog: an 8×8 output-stationary systolic array at 64 int4 MACs/cycle, a SIMD vector unit, and a DMA engine over a 64 KB scratchpad and 512 KB external SRAM, driven by a PicoRV32 core running bare-metal C firmware over AXI MMIO. On a Cmod A7 (Artix-7, 12 MHz) it hits 248 ms to first token and 58 ms/token during decode. Roofline analysis drove the optimization pass — double-buffered weights to overlap DMA with compute, plus operator fusion — for a 51% speedup in prefill and 19% overall. [writeup](/transformer-tpu/) · [code](https://github.com/im-afan/transformer-tpu-int4)

## Research

**SumCATS — GPU sum-check over binary fields** — GMU ASSIP, under Prof. Tanvir Arafin, Summer 2025

First-authored a paper accepted to and presented at IEEE DATE 2026 (25% acceptance, double-blind) on a CUDA implementation of the sum-check protocol over binary fields, a key step in modern zero-knowledge proofs. It reaches 1.81× speedup on an RTX 3090 Ti and 1.62× on an A100 over the previous best GPU implementation, using bitsliced batching, shared-memory reductions, and a per-round operation count derived to decide analytically when to switch algorithms. A later memory-bound optimization trades memory for compute by recomputing batches, lifting A100 speedup from 1.41× to 1.62×. [paper](https://doi.org/10.23919/DATE69613.2026.11539722) · [code](https://github.com/SPIRE-GMU/sum_cats)

## Engineering Leadership

**FIRST Robotics Competition — Paly Robotics (Team 8), Software Lead** — Fall 2022 – Summer 2026

Led a 12-person software subteam for a world top-200 robot, owning technical direction across 8 subsystems (~7K lines of Java) and reviewing all contributors' code; led the team to its first event win in 6 years at the 2026 Contra Costa District event. Profiled the robot code in VisualVM, traced the dominant per-cycle cost to NetworkTables reads from four Limelight coprocessors, and replaced the every-camera-every-cycle query with a round-robin schedule — safe because the fusion layer merges by timestamp, not arrival order. Also spearheaded a rewrite onto an event-driven architecture with a central state store, putting every subsystem behind an interface with real and simulated implementations so issues could be debugged on a laptop.

## Education

**University of California, Los Angeles** — B.S. Electrical Engineering, expected Jun 2030

Regents Scholar (merit-based, top 1% of incoming class); ECE Fast Track Program (top 10% of incoming ECE students). Dual enrollment at Foothill College: multivariable calculus, linear algebra, differential equations, discrete math.

## Honors

- USA Computing Olympiad, Platinum Division; perfect score (1000/1000) in the 2023 December Gold contest
- Codeforces Expert, peak rating 1874

## Skills

- **Languages** — C/C++, SystemVerilog, CUDA, Python, Java
- **Tools** — Vivado, Icarus Verilog, Make, CMake, Git, Linux
- **ML** — PyTorch, NumPy, quantization-aware training
- **Areas** — Computer architecture, RTL design, bare-metal firmware, parallel programming, LLM training & inference, algorithms & data structures
