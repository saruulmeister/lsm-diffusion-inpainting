# Diffusion-Based Inpainting for Structured Missing Data in Light-Sheet Microscopy

**Saruultugs Batbayar**

This repository serves as a **research hub** for my work on diffusion-based image restoration,
with a focus on **structured missing data** arising in **Light Sheet Microscopy (LSM)**.
It consolidates reports, experiments, and results across multiple stages of the project.

---

## Research Motivation
Light Sheet Microscopy enables fast, low-phototoxic imaging of live samples,
but introduces **severe stripe-like row missing artifacts** due to acquisition constraints.
Reconstructing full images or volumes under extreme undersampling requires models that:
- Respect known measurements
- Preserve global structure
- Remain stable with very limited visible data

Diffusion models provide a principled framework to address this problem.

---

## Projects (Chronological)

### 1. PatchDDM-Based Image Inpainting on CelebA (Foundational)
**Goal:** Understand DDPM fundamentals, patch-based masking, and RePaint sampling.

- Implemented UNet-based DDPM with time embedding
- Trained on patch-masked CelebA faces (64×64)
- Explored RePaint-style sampling with pixel reinjection
- Identified limitations of unconditional diffusion under structured loss

📄 Report: `docs/first.pdf`

---

### 2. PatchDDM-Based Inpainting on CelebA (Extended)
**Goal:** Validate training behavior and qualitative reconstruction.

- Custom PatchMaskDataset
- Visualization of masked → reconstructed → ground truth
- Verified learning via controlled overfitting experiments

📄 Report: `docs/second.pdf`

---

### 3. Leveraging Diffusion Models for LSM Image Restoration
**Goal:** Transition from patch masking to **stripe-based structured masking**.

- Implemented SparseRowMasker with controllable missing ratios (50%–85%)
- Applied SD-Inpaint + ControlNet (Canny / soft-edge)
- Generated control images from pseudo-full interpolations to avoid stripe leakage
- Studied system constraints (batch size, memory limits)

📄 Report: `docs/third.pdf`

---

### 4. Diffusion-Based Reconstruction with DPS
**Goal:** Compare conditioning and inverse-problem formulations.

Models evaluated:
- RePaint
- CoPaint / Tiramisu
- DPS (Diffusion Posterior Sampling)
- ControlNet + DPS (proposed)

Key insight:
> Conditioning improves structure, DPS enforces measurement consistency;
> combining both yields the most robust reconstructions.

📄 Report: `docs/forth.pdf`

---

### 5. Stripe-Mask Inpainting with Trained ControlNet
**Goal:** Train a **custom ControlNet** for stripe-mask inpainting.

- 43,525 COCO images
- Dynamic online stripe-mask generation
- 4-channel ControlNet conditioning
- SD 1.5 UNet / VAE / text encoder frozen
- Quantitative evaluation (SSIM, LPIPS)

📄 Report: `docs/fifth.pdf`

---

## Repository Contents
- `docs/` → All progress reports submitted to advisor
- `figures/` → Key qualitative results
- Code repositories:
  - ControlNet
  - ControlNet Canny
  - DPS
  - CoPaint
  - RePaint
  - StrDiffusion  
  (maintained separately; links available upon request)

---

## Summary
This repository documents a **progressive research trajectory**:
> DDPM fundamentals → patch inpainting → structured stripe masking → inverse diffusion → custom ControlNet training

It reflects both **theoretical understanding** and **practical system-level implementation**
for diffusion-based reconstruction under extreme information loss.
