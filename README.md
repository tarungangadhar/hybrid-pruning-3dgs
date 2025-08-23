# Hybrid Pruning for 3D Gaussian Splatting (3DGS)

Practical framework to **prune** 3D Gaussian Splatting scenes using a **hybrid ranking signal** (SH energy, multi-view projected area, visibility, local density) with robust normalization and simple post-cleanup. Goal: **sharply reduce size** while **preserving visual quality**.

> 📄 Full write-up: see [`docs/HybridPruningFramework3DGSFinalized.pdf`](docs/HybridPruningFramework3DGSFinalized.pdf)

---

## Why

Single-signal pruning (e.g., opacity or area only) often:
- keeps background blobs (“floaters”),
- over-smooths edges / thin structures,
- or collapses texture detail.

A fused ranking is more stable across scenes and viewpoints.

---

## Features

- **Signals used per splat**
  - **SH Energy** (DC + higher orders, sigmoid-linearized)
  - **Projected Area (multi-view)** via camera intrinsics & per-axis scale projection
  - **Visibility proxy** (depth-aware footprint)
  - **Local Density** (kNN in splat space)
- **Experiments**: opacity/energy/area baselines vs **Hybrid**
- **Outputs**: pruned PLY, rate–distortion plots (PSNR vs kept fraction), qualitative comparisons, point-cloud previews

---

## Quickstart (Colab-friendly)

This project was developed in **Google Colab**.

**Dependencies (installed in code):**
