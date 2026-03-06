
# Pathwise Test-Time Correction for Autoregressive Long Video Generation

[![Paper](https://img.shields.io/badge/Paper-ArXiv-red.svg)](https://arxiv.org/abs/2602.05871)
[![Project Page](https://img.shields.io/badge/Project-Page-blue.svg)](#)
[![GitHub](https://img.shields.io/badge/Code-GitHub-black.svg)](https://github.com/404)

> **Pathwise Test-Time Correction (TTC)** is a training-free framework designed to suppress error accumulation in autoregressive long video generation.  
> By performing correction directly along the diffusion sampling trajectory, TTC stabilizes long-horizon generation while preserving the natural dynamics of diffusion transitions.

**Xunzhi Xiang\*<sup>1,2</sup>, Zixuan Duan\*<sup>1</sup>, Guiyu Zhang<sup>3</sup>, Haiyu Zhang<sup>2</sup>,  
Zhe Gao<sup>1</sup>, Junta Wu<sup>2</sup>, Shaofeng Zhang<sup>4</sup>,  
Tengfei Wang<sup>†2</sup>, Qi Fan<sup>†1</sup>, Chunchao Guo<sup>2</sup>**

<sup>1</sup> Nanjing University  
<sup>2</sup> Tencent Hunyuan  
<sup>3</sup> Chinese University of Hong Kong, Shenzhen  
<sup>4</sup> University of Science and Technology of China  

\* Equal contribution  
† Corresponding authors

---

## 📖 Overview

Autoregressive video diffusion models enable scalable long video generation but often suffer from **severe error accumulation**, causing visual drift and structural inconsistency over time.

We propose **Test-Time Correction (TTC)**, a **training-free inference strategy** that stabilizes long-horizon autoregressive generation by correcting the sampling trajectory during diffusion inference.

Our key observation is that **diffusion trajectories exhibit a natural phase transition**:

- **High-noise regime** determines the **global structure** of the frame.
- **Low-noise regime** refines **appearance and texture details**.

TTC leverages this property by applying corrections **only during the appearance refinement stage**, ensuring that global scene structure remains intact.

The correction procedure operates in three stages:

1. **Reference-guided correction**  
   The predicted frame is re-noised and re-denoised using the initial frame as a stable reference anchor.

2. **Noise-level restoration**  
   The corrected prediction is re-noised back to the current diffusion timestep using fresh Gaussian noise.

3. **Context-aware re-denoising**  
   The frame is re-denoised again using the original autoregressive context to maintain temporal continuity.

Because TTC operates **entirely along valid diffusion transitions**, it avoids abrupt state perturbations and introduces **minimal computational overhead**, while effectively suppressing long-term drift.

---

## 🎥 Comparison Videos

Hover on the videos to see corresponding prompts and drag the progress bar to inspect temporal consistency.

---

## 📌 Framework

![Framework](assets/pipeline.png)
