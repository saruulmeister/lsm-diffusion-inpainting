# Diffusion-Based Inpainting for Structured Missing Data in Light-Sheet Microscopy

Saruultugs

This repository is a **research hub** for my work on diffusion-based image restoration, specifically for **structured missing data** present in **Light Sheet Microscopy (LSM)**.

It records an increasingly complex research process from basic diffusion-based inpainting to personal training of ControlNet on extreme undersampling.

---
# Research Motivation
Researchers
Light Sheet Microscopy allows fast and low phototoxic imaging of living samples, while imposing **severe stripe-like row missing artifacts**.
To reconstruct complete images/volumes from such conditions, models should ideally possess the following properties:
* RESPECT KNOWN MEASUREMENT

- Global structure retained

→ Stable with very limited data being visible

Diffusion Models offer a rigorous framework to treat this issue.

---

## Projects (Chronological)
### 1. Diffusion Inpainting on CelebA - First Exploration

**Goal:** Evaluation of existing diffusion-based inpainting algorithms on the masked data.

- Tested PatchDDPM inpainting on faces from the CelebA dataset (patch-mask

- Tested RePaint-style sampling with pixel reinjection

- Investigated limitations in unconditional diffusion models for structured missing regions and large missing areas
# Report: `docs/
---

### 2. Diffusion Inpainting on CelebA — Extended Experiments

**Goal:** Training behavior and quality validation.

- Introduced a custom dataset: PatchMaskDataset

- Trained a UNet-based DDPM on masked inputs with time embeddings
- Masked input visuals → reconstructed visuals → ground truths
- Demonstrated the correctness of learned solutions by controlled overfitting experimentation

???? Report File:

---

### 3. Diffusion Models Usage in LSM Image Restoration

*   **Goal:** Move on from the masking by patches stage to the masking by stripes, which are in consideration of
- Added SparseRowMasker with adjustable ratios (50%–85%) for
- Used Stable Diffusion Inpainting with Control Net (Canny/soft edge)
- Created control images through pseudo-full interpolation to prevent stripe leakage

- Identified system constraints regarding batch sizes and memory.

???? Report: `

-

### 4. Reconstruction by Diffusion using DPS

*Goal:*
     Compare the conditioning and inverse problem formulations
Models explored:
- RePaint
- CoPaint / Tiramisu

- DPS (Diffusion Posterior Sampling)

- ControlNet + DPS (proposed)

Key Insight:

Conditioning refines structure, while enforcement of DPS maintains the measurement consistency; together, these two produce the best reconstruction results.

???? Report: ` <div ### 5. Stripe-Mask Inpainting via ControlNet Training **Goal:** Develop a learned ControlNet that will perform structured stripe masks. - 43,525 COCO train images * Dynamic online stripe mask generation. - ControlNet Conditioning, - Stable Diffusion 1.5 UNet / VAE / text encoder frozen - Quantitative Comparison by SSIM & LPIPS ???? Report: ` --- # Summary This work shows a **coherent research progression**: > Baseline Diffusion Process → Patch Inpainting → Structured Stripe Masking → Inverse Diffusion (DPS) → Custom ControlNet Training This repository combines reports and results that show **theoretical understanding** and **system-level implementation** in reconstructing using diffusion on extreme information loss.
