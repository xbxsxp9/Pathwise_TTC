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

<table>
  <tr>
    <th width="27%" align="center">Wan2.1</th>
    <th width="27%" align="center">VideoJAM</th>
    <th width="30%" align="center">DreamWorld (Ours)</th>
    <th width="16%" align="center">Prompt</th>
  </tr>
  <tr>
    <td><video src="https://github.com/user-attachments/assets/36a02d9b-2dd6-40b5-ae7e-1c6e47cac746" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/0ba95548-a249-4a79-b057-42a4034401c6" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/6b35a1ce-375e-4077-a852-074a216b35b3" autoplay loop muted playsinline width="100%"></video></td>
    <td align="center" valign="middle">Gwen Stacy reading a book, tilt up.</td>
  </tr>
  <tr>
    <td><video src="https://github.com/user-attachments/assets/487ee0b8-7ba6-4281-9550-07e7ec4daddd" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/e123ef42-0d6a-41a2-a8a0-e67ed8402ab2" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/5589d7d7-18db-42a3-9c1d-8c0d0a64b82d" autoplay loop muted playsinline width="100%"></video></td>
    <td align="center" valign="middle">A person is picking up the phone.</td>
  </tr>
  <tr>
    <td><video src="https://github.com/user-attachments/assets/f6f48d08-f629-46e1-8b81-6c03c91d65b0" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/e2ae9f2d-50ed-4bb8-b2c1-0cda19df8a9a" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/eea8924e-171f-4eb0-b865-97b16efc743a" autoplay loop muted playsinline width="100%"></video></td>
    <td align="center" valign="middle">A cup of tea is tilted in the space station...</td>
  </tr>
  <tr>
    <td><video src="https://github.com/user-attachments/assets/71f57bc0-11c2-4fba-bf6a-7844d09da597" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/16609298-48d6-4275-8e48-2191d349b8cb" autoplay loop muted playsinline width="100%"></video></td>
    <td><video src="https://github.com/user-attachments/assets/3f5311f4-e1dd-4ff9-b4e9-cd0bc17268c9" autoplay loop muted playsinline width="100%"></video></td>
    <td align="center" valign="middle">Happy dog wearing a yellow turtleneck...</td>
  </tr>
</table>


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
