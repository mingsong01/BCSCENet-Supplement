# CARAFE Ablation

<p align="center"><img src="../assets/readme_accent.svg" alt="" width="100%"></p>

## Overview

This experiment investigates the effects of Content-Aware ReAssembly of FEatures (CARAFE) and Differentiable Planar Background Suppression (DPBS) on infrared small target detection performance. The evaluation is conducted on the IRSTD-1K dataset using three metrics: mean Intersection over Union (mIoU), probability of detection (Pd), and false alarm rate (Fa).

## Experimental Setup

Four configurations are evaluated by independently enabling or disabling CARAFE and DPBS while retaining the Structure Tensor Anisotropy Gate (STAG) and Local Contrast Residual Enhancement (LCRE) modules. This controlled comparison examines the individual and combined effects of CARAFE and DPBS within the BCSCENet architecture.

## Quantitative Results

| CARAFE | DPBS | STAG | LCRE | mIoU (%) ↑ | Pd (%) ↑  | Fa (×10⁻⁶) ↓ |
| ------ | ---- | ---- | ---- | ---------- | --------- | ------------ |
| ×      | ×    | ✓    | ✓    | 67.23      | 92.86     | 11.77        |
| ✓      | ×    | ✓    | ✓    | 67.14      | 92.18     | 18.22        |
| ×      | ✓    | ✓    | ✓    | 68.50      | 93.20     | 8.05         |
| ✓      | ✓    | ✓    | ✓    | **70.05**  | **93.54** | **7.74**     |

*✓ and × indicate whether the corresponding component is enabled or disabled, respectively.*

## Results and Analysis

Without DPBS, introducing CARAFE decreases mIoU from 67.23% to 67.14% and Pd from 92.86% to 92.18%, while increasing Fa from 11.77 to 18.22 × 10⁻⁶. In contrast, when DPBS is enabled, introducing CARAFE improves mIoU from 68.50% to 70.05% and Pd from 93.20% to 93.54%, while reducing Fa from 8.05 to 7.74 × 10⁻⁶.

The performance degradation observed when CARAFE is used without DPBS may be associated with insufficient suppression of background interference before feature reassembly. By estimating and suppressing smooth background trends, DPBS may reduce the influence of background responses on subsequent content-aware upsampling.

The combined configuration achieves the highest mIoU (70.05%) and Pd (93.54%), together with the lowest Fa (7.74 × 10⁻⁶). These results indicate that the effectiveness of CARAFE depends on the accompanying background suppression configuration, with the combination of CARAFE and DPBS providing the best overall performance among the evaluated settings.

---

[Back to the supplementary materials overview](../)
