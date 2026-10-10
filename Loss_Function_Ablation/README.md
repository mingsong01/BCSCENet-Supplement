# Loss Function Ablation

*Evaluation of nine loss configurations on IRSTD-1K*

<p align="center"><img src="../assets/readme_accent.svg" alt="" width="100%"></p>

## Overview

This experiment evaluates the influence of different loss functions and their combinations on infrared small target detection performance.

BCSCENet employs SLSIoU Loss and Weighted Binary Cross-Entropy (BCE) Loss. SLSIoU strengthens the overlap constraint between predicted and ground-truth regions and increases sensitivity to target scale and localization differences. Weighted BCE increases the contribution of positive pixels to address foreground–background pixel imbalance.

## Experimental Setup

The experiments are conducted on IRSTD-1K.

All configurations use the same network architecture, dataset split, optimizer, training strategy, and evaluation protocol. The loss function is varied to examine its influence on detection performance.

## Quantitative Results

| Loss Function             | mIoU (%) ↑ | Pd (%) ↑  | Fa (×10⁻⁶) ↓ |
| ------------------------- | ---------- | --------- | ------------ |
| BCE                       | 64.83      | 88.10     | 9.56         |
| Weighted BCE              | 56.24      | 93.88     | 29.30        |
| Dice Loss                 | DNC        | DNC       | DNC          |
| Dice + Weighted BCE       | 68.60      | 91.84     | 10.25        |
| Focal Loss                | 60.86      | 90.48     | 14.50        |
| Tversky Loss              | DNC        | DNC       | DNC          |
| Tversky + Weighted BCE    | 66.99      | 92.86     | 13.06        |
| SLSIoU Loss               | 66.90      | **94.56** | 15.79        |
| **SLSIoU + Weighted BCE** | **70.05**  | 93.54     | **7.74**     |

**DNC** indicates that the corresponding loss function did not converge under the common training setting.

## Analysis

The experimental results demonstrate that different loss functions produce different trade-offs among segmentation accuracy, target detection probability, and false alarm rate.

SLSIoU Loss alone achieves the highest Pd of 94.56%, while the combination of SLSIoU and Weighted BCE achieves the highest mIoU of 70.05% and the lowest Fa of 7.74 × 10⁻⁶.

Under the evaluated training setting, SLSIoU + Weighted BCE provides the most favorable overall performance among the tested loss configurations.

---

[Back to the supplementary materials overview](../)
