# Diffusion-Based Inpainting for Structured Missing Data in Light-Sheet Microscopy

** Saruultugs Batbayar **

This repository serves as a research point for my work on image restoration through diffusion on structured missing data samples in the context of Light Sheet Microscopy.
It tracks a progressive line of inquiry, which moved from baseline diffusion inpainting to personal ControlNet training with extreme undersampling.
---


## Research Motivation
Fast imaging with reduced phototoxic effects in living specimens is possible with Light Sheet Microscopy, while it creates strong stripe artifacts for missing rows because of data-acquisition issues.
Reconstructing images or volumes in these conditions requires the following from the models:

- Respect known measurements
- Preserve Global Structure
- Stable with little data in sight

A diffusion model offers a sound approach to solve this issue.
---

##  Projects (Chronological)

### 1. Diffusion Inpainting on CelebA - First Experiences

**Task:** Analyze the performance of existing diffusion-based inpainting models on the masked data.

- Tested Patch DDPM inpainting on faces of size 64×64 with a mask
- Evaluated RePaint sampling method with pixel reinjection
– Examined the limitations of unconditional diffusion in the presence of structured or large missing regions

### 2. Diffusion Inpainting on CelebA — Extended Experiments

**Aim:** Validate training process behavior, reconstruction quality.
- Developed a custom PatchMaskDataset
- Trained a UNet-based DDPM on masked inputs and learned time embeddings.

- Masked image → reconstructed image → ground truth results

- Demonstrated correct learning by controlled overfitting tests
### 3. Utilizing Diffusion Models in LSM Image Restoration
**Purpose:** To move from the current method that uses patch masking to a new technique based on stripe masking that corresponds to the
- Applied SparseRowMasker with controllable missing rates (50%-85%)

- Used Stable Diffusion Inpainting with ControlNet (Canny/soft-edge edges)

* Produced control images using pseudo-full interpolation to prevent stripe leakage

- Informed about system constraints (batch size, memory constraints)
### 4. Reconstruction Using DPS by Diffusion
***Goal:*** Comparison between formulations of conditioning and inverse problems.
Models explored:

- RePaint

- CoPaint / Tiramisu

- DPS (Diffusion Posterior Sampling) - ControlNet + DPS Bromdum Key insight:
The Conditioning helps with structure, while the enforcement of measurements by DPS ensures consistency in the measurements, and a combination of both ensures the most reliable recon ### 5. Stripe-Mask Inpainting with Trained * Task: Train a custom ControlNet for structured stripe-mask inpainting. - Trained on 43,525 COCO Images - Dynamic online stripe mask generation - 4-channel ControlNet Conditioning - Stable Diffusion 1.5 UNet/VAE/text encoder frozen - SSIM and LPIPS-Based Quantitative Assessment Introduction This work offers a consistent approach to doing research and presents a well- > Baseline Diffusion + Patch inpainting + Structured Stripe Masking + Inverse diffusion (DPS) + ControlNet training_Customized This repository integrates the various reports and results that support theoretical knowledge and system-level implementation of diffusion-based reconstruction in adverse conditions of information loss.
