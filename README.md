# Pathwise Test-Time Correction for Autoregressive Long Video Generation

<p align="center">
  <a href="https://arxiv.org/abs/2602.05871">
    <img src="https://img.shields.io/badge/Paper-ArXiv-red.svg" alt="Paper">
  </a>
  <a href="https://ttc-1231.github.io/">
    <img src="https://img.shields.io/badge/Demo-Project_Page-green.svg" alt="Demo">
  </a>
  <a href="https://github.com/404">
    <img src="https://img.shields.io/badge/Code-GitHub-black.svg" alt="Code">
  </a>
</p>

<p align="center">
  <strong>A training-free framework for suppressing error accumulation in autoregressive long video generation.</strong>
</p>

<p align="center">
  Xunzhi Xiang, Zixuan Duan, Guiyu Zhang, Haiyu Zhang, Zhe Gao, Junta Wu,
  Shaofeng Zhang, Tengfei Wang, Qi Fan, Chunchao Guo
</p>

<p align="center">
  <a href="https://ttc-1231.github.io/">🌐 <strong>Project Page</strong></a> &nbsp;|&nbsp;
  <a href="https://arxiv.org/abs/2602.05871">📄 <strong>Paper</strong></a> &nbsp;|&nbsp;
  <a href="https://ttc-1231.github.io/">🎬 <strong>Demo</strong></a>
</p>

---

## ✨ Overview

Autoregressive video diffusion models enable scalable long-horizon video generation, but they often suffer from **error accumulation**, leading to visual drift and structural inconsistency over time.

We propose **Pathwise Test-Time Correction (TTC)**, a **training-free inference framework** that mitigates long-term drift by correcting the diffusion sampling trajectory during autoregressive generation.

Our key observation is that the diffusion trajectory naturally exhibits two distinct regimes:

- **High-noise stages** primarily determine the **global structure** of generated frames.
- **Low-noise stages** mainly refine **appearance and texture details**.

Based on this observation, TTC applies correction **only during the appearance refinement stage**, after the global structure has already stabilized. The correction is performed directly along the **valid diffusion transition path**, preserving the consistency of the generative dynamics while maintaining temporal coherence.

As a result, TTC effectively suppresses long-horizon error accumulation with only **minimal computational overhead**.

---

## 🧩 Framework

<p align="center">
  <img src="assets/pipeline.png" alt="TTC framework" width="95%">
</p>

TTC performs **pathwise correction** during diffusion inference through three stages:

1. **Reference-guided correction**  
   The predicted frame is re-noised and re-denoised using the initial frame as a stable visual anchor.

2. **Noise-level restoration**  
   The corrected prediction is re-noised back to the current diffusion timestep with fresh Gaussian noise.

3. **Context-aware re-denoising**  
   The frame is denoised again using the original autoregressive context to ensure smooth temporal integration.

This pathwise correction strategy avoids abrupt state perturbations and preserves the intrinsic diffusion dynamics, enabling more stable long-duration video generation.

---

## 🎬 Demo Video

<p align="center">
  <table>
    <tr>
      <th width="40%" align="center">Demo Video</th>
      <th width="60%" align="center">Prompt</th>
    </tr>
    <tr>
      <td>
        <video src="assets/demo.mp4" autoplay loop muted playsinline width="100%"></video>
      </td>
      <td align="center" valign="middle">
        Gwen Stacy reading a book, tilt up.
      </td>
    </tr>
  </table>
</p>


More qualitative results and comparison videos are also available on the [project page](https://ttc-1231.github.io/).

---

## 📚 Citation

If you find this work useful, please consider citing:

```bibtex
@article{xiang2026ttc,
  title={Pathwise Test-Time Correction for Autoregressive Long Video Generation},
  author={Xiang, Xunzhi and Duan, Zixuan and Zhang, Guiyu and Zhang, Haiyu and Gao, Zhe and Wu, Junta and Zhang, Shaofeng and Wang, Tengfei and Fan, Qi and Guo, Chunchao},
  journal={arXiv preprint arXiv:2602.05871},
  year={2026}
}
