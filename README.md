# Pathwise Test-Time Correction for Autoregressive Long Video Generation

<p align="center">
  <a href="https://arxiv.org/abs/2602.05871">
    <img src="https://img.shields.io/badge/Paper-ArXiv-red.svg">
  </a>
  <a href="https://ttc-1231.github.io/">
    <img src="https://img.shields.io/badge/Demo-Project_Page-green.svg">
  </a>
  <a href="https://github.com/404">
    <img src="https://img.shields.io/badge/Code-GitHub-black.svg">
  </a>
</p>

<p align="center">
Xunzhi Xiang, Zixuan Duan, Guiyu Zhang, Haiyu Zhang, Zhe Gao, Junta Wu,  
Shaofeng Zhang, Tengfei Wang, Qi Fan, Chunchao Guo
</p>

---

## 🌐 Project Page

Explore more qualitative results and videos on our project page:

**https://ttc-1231.github.io/**

---

## 📖 Overview

Autoregressive video diffusion models enable scalable **long-horizon video generation**, but they often suffer from **error accumulation**, which leads to visual drift and structural inconsistency over time.

We propose **Pathwise Test-Time Correction (TTC)**, a **training-free inference framework** that mitigates long-term drift by correcting the diffusion sampling trajectory during autoregressive generation.

Our key observation is that the diffusion trajectory naturally exhibits two regimes:

- **High-noise stages** determine the **global structure** of generated frames.
- **Low-noise stages** refine **appearance and texture details**.

Based on this observation, TTC performs correction **only during the appearance refinement stage**, after the global structure has stabilized.  
The correction is applied directly along the **valid diffusion transition path**, ensuring that the generative dynamics remain consistent while maintaining temporal coherence.

As a result, TTC effectively suppresses long-horizon error accumulation while introducing **minimal computational overhead**.

---

## ⚙️ Framework

<p align="center">
  <img src="assets/pipeline.png" width="95%">
</p>

The TTC framework performs **pathwise correction** during diffusion inference through three stages:

1. **Reference-guided correction**  
   The predicted frame is re-noised and re-denoised using the initial frame as a stable visual anchor.

2. **Noise-level restoration**  
   The corrected prediction is re-noised back to the current diffusion timestep using fresh Gaussian noise.

3. **Context-aware re-denoising**  
   The frame is denoised again using the original autoregressive context to ensure smooth temporal integration.

This pathwise correction strategy avoids abrupt state perturbations and preserves the intrinsic diffusion dynamics, enabling stable **long-duration video generation**.

---

## 🎥 Demo

More qualitative results and comparison videos can be found on the project page:

https://ttc-1231.github.io/

---

## 📜 Citation

If you find this work useful, please consider citing:

```bibtex
@article{xiang2026ttc,
  title={Pathwise Test-Time Correction for Autoregressive Long Video Generation},
  author={Xiang, Xunzhi and Duan, Zixuan and Zhang, Guiyu and Zhang, Haiyu and Gao, Zhe and Wu, Junta and Zhang, Shaofeng and Wang, Tengfei and Fan, Qi and Guo, Chunchao},
  journal={arXiv preprint arXiv:2602.05871},
  year={2026}
}
