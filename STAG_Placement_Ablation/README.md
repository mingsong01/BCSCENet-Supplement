# STAG Placement Ablation

*Evaluation of STAG placement across four decoder stages*

<p align="center"><img src="../assets/readme_accent.svg" alt="" width="100%"></p>

## Overview

This experiment investigates the influence of Structure Tensor Anisotropy Gate (STAG) placement on infrared small target detection performance.

STAG is designed to suppress structured background interference with directional characteristics, including edge-like and stripe-like patterns.

The evaluation compares different placements of STAG across the four decoder stages of BCSCENet.

## Experimental Configurations

The decoder stages correspond to the following spatial resolutions:

- **D3:** 1/8 resolution.
- **D2:** 1/4 resolution.
- **D1:** 1/2 resolution.
- **D0:** Full resolution.

Five configurations are evaluated: no STAG, earlier-stage placement, the proposed intermediate-stage placement, later-stage placement, and placement at all four stages.

## Quantitative Results

The experiments are conducted on IRSTD-1K.

| Setting                                 | D3 (1/8) | D2 (1/4) | D1 (1/2) | D0 (1/1) | mIoU (%) ↑ | Pd (%) ↑  | Fa (×10⁻⁶) ↓ |
| --------------------------------------- | -------- | -------- | -------- | -------- | ---------- | --------- | ------------ |
| STAG not used                           | ×        | ×        | ×        | ×        | 67.42      | 92.52     | 14.88        |
| Earlier-stage placement                 | ✓        | ✓        | ×        | ×        | 67.77      | 93.20     | 16.02        |
| **Intermediate-stage placement (Ours)** | ×        | ✓        | ✓        | ×        | **70.05**  | **93.54** | **7.74**     |
| Later-stage placement                   | ×        | ×        | ✓        | ✓        | 68.35      | 89.80     | 8.27         |
| All-stage placement                     | ✓        | ✓        | ✓        | ✓        | 68.66      | 91.84     | 8.88         |

The checkmark indicates that STAG is enabled at the corresponding decoder stage.

## Analysis

The intermediate-stage configuration, with STAG applied at D2 and D1, achieves the highest mIoU and Pd and the lowest Fa among the evaluated placements.

Earlier-stage placement increases Fa to 16.02 × 10⁻⁶, whereas later-stage placement reduces Pd to 89.80%. Applying STAG at all decoder stages does not provide further improvement over the intermediate-stage configuration.

These results support the placement of STAG at the second and third decoder stages of BCSCENet.

---

[Back to the supplementary materials overview](../)
