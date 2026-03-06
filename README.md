
# Pathwise Test-Time Correction for Autoregressive Long Video Generation

[![Paper](https://img.shields.io/badge/Paper-ArXiv-red.svg)](https://arxiv.org/abs/2602.05871)
[![Project Page](https://img.shields.io/badge/Project-Page-blue.svg)](#)
[![GitHub](https://img.shields.io/badge/Code-GitHub-black.svg)](https://github.com/404)

> **Pathwise Test-Time Correction (TTC)** is a training-free framework designed to suppress error accumulation in autoregressive long video generation..<br>
**Xunzhi Xiang\*<sup>1,2</sup>, Zixuan Duan\*<sup>1</sup>, Guiyu Zhang<sup>3</sup>, Haiyu Zhang<sup>2</sup>,  Zhe Gao<sup>1</sup>, Junta Wu<sup>2</sup>, Shaofeng Zhang<sup>4</sup>,  Tengfei Wang<sup>†2</sup>, Qi Fan<sup>†1</sup>, Chunchao Guo<sup>2</sup>**

---

## 📖 Overview

Autoregressive video diffusion models enable scalable long video generation but often suffer from **severe error accumulation**, causing visual drift and structural inconsistency over time. We propose **Test-Time Correction (TTC)**, a **training-free inference strategy** that stabilizes long-horizon autoregressive generation by correcting the sampling trajectory during diffusion inference.

![Framework](assets/pipeline.png)

---
