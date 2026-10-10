# Cross-Dataset Evaluation

*Bidirectional evaluation between IRSTD-1K and NUAA-SIRST*

<p align="center"><img src="../assets/readme_accent.svg" alt="" width="100%"></p>

## Overview

This experiment evaluates the cross-dataset generalization performance of BCSCENet on IRSTD-1K and NUAA-SIRST.

The evaluation considers differences in target distributions, target scales, target morphology, and background complexity between the two datasets.

## Evaluation Settings

Bidirectional cross-dataset evaluation is conducted using the weights trained on each source dataset.

Two cross-dataset configurations are considered:

1. Training on IRSTD-1K and evaluating on NUAA-SIRST.
2. Training on NUAA-SIRST and evaluating on IRSTD-1K.

Within-dataset results on IRSTD-1K and NUAA-SIRST are also included for comparison.

## Quantitative Results

| Training Set | Testing Set | mIoU (%) ↑ | Pd (%) ↑ | Fa (×10⁻⁶) ↓ |
| ------------ | ----------- | ---------- | -------- | ------------ |
| IRSTD-1K     | IRSTD-1K    | 70.05      | 93.54    | 7.74         |
| IRSTD-1K     | NUAA-SIRST  | 64.50      | 91.74    | 6.92         |
| NUAA-SIRST   | NUAA-SIRST  | 78.65      | 100.00   | 1.60         |
| NUAA-SIRST   | IRSTD-1K    | 58.02      | 86.73    | 42.21        |

## Analysis

When trained on IRSTD-1K and evaluated on NUAA-SIRST, BCSCENet achieves an mIoU of 64.50%, a Pd of 91.74%, and an Fa of 6.92 × 10⁻⁶.

In the reverse direction, training on NUAA-SIRST and evaluating on IRSTD-1K yields an mIoU of 58.02%, a Pd of 86.73%, and an Fa of 42.21 × 10⁻⁶.

The results demonstrate that BCSCENet retains target detection capability under cross-dataset distribution changes.

However, transferring weights trained on NUAA-SIRST to the more complex IRSTD-1K dataset results in a more pronounced performance reduction. This indicates limitations in generalization when training is performed on a dataset with a relatively simpler target and background distribution.

---

[Back to the supplementary materials overview](../)
