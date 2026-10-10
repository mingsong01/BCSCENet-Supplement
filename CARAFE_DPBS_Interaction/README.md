# CARAFE–DPBS Interaction

*Analysis of background suppression and content-aware upsampling*

<p align="center"><img src="../assets/readme_accent.svg" alt="" width="100%"></p>

## Overview

This experiment investigates the interaction between Content-Aware ReAssembly of FEatures (CARAFE) and Differentiable Planar Background Suppression (DPBS) in BCSCENet.

CARAFE performs content-aware feature reassembly during upsampling, whereas DPBS estimates and suppresses smooth background trends in the feature domain.

The evaluation examines how different combinations of CARAFE and DPBS influence segmentation accuracy, target detection probability, and false alarm rate.

## Experimental Configurations

Four configurations are evaluated on IRSTD-1K.

STAG and LCRE remain enabled, while CARAFE and DPBS are independently included or excluded.

## Quantitative Results

| CARAFE | DPBS | STAG | LCRE | mIoU (%) ↑ | Pd (%) ↑  | Fa (×10⁻⁶) ↓ |
| ------ | ---- | ---- | ---- | ---------- | --------- | ------------ |
| ×      | ×    | ✓    | ✓    | 67.23      | 92.86     | 11.77        |
| ✓      | ×    | ✓    | ✓    | 67.14      | 92.18     | 18.22        |
| ×      | ✓    | ✓    | ✓    | 68.50      | 93.20     | 8.05         |
| ✓      | ✓    | ✓    | ✓    | **70.05**  | **93.54** | **7.74**     |

## Interaction Analysis

When DPBS is absent, introducing CARAFE decreases mIoU from 67.23% to 67.14% and Pd from 92.86% to 92.18%, while increasing Fa from 11.77 to 18.22 × 10⁻⁶.

When DPBS is enabled, introducing CARAFE increases mIoU from 68.50% to 70.05% and Pd from 93.20% to 93.54%, while reducing Fa from 8.05 to 7.74 × 10⁻⁶.

The results demonstrate that CARAFE produces different performance effects depending on the presence of DPBS.

## Discussion

The performance degradation associated with CARAFE in the absence of DPBS may be related to insufficient suppression of background interference in the input features.

CARAFE generates content-dependent reassembly kernels and aggregates neighboring features during upsampling. When background interference is prominent, background-related responses may also participate in the feature reassembly process, affecting the distinction between small targets and their surrounding regions.

DPBS estimates and suppresses smooth background trends before the subsequent feature reassembly process, potentially reducing the influence of background interference.

The experimental results are consistent with a beneficial interaction between background suppression and content-aware upsampling in the evaluated BCSCENet configurations.

---

[Back to the supplementary materials overview](../)
