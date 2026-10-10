# Optimizer Comparison

*Comparison of five optimizer configurations on IRSTD-1K*

<p align="center"><img src="../assets/readme_accent.svg" alt="" width="100%"></p>

## Overview

This experiment evaluates the influence of different optimizer configurations on the performance of BCSCENet.

The evaluated optimizers include Adam, AdamW, SGD, and AdaGrad. Two AdamW configurations with different learning rates are considered.

The AdaGrad configuration follows the optimizer setting adopted in MSHNet.

## Experimental Setup

The comparison is conducted on the IRSTD-1K dataset.

Except for the optimizer, learning rate, and weight decay, all other training and evaluation settings are kept consistent with the implementation settings of BCSCENet.

## Quantitative Results

| Optimizer   | Learning Rate | Weight Decay | mIoU (%) ↑ | Pd (%) ↑  | Fa (×10⁻⁶) ↓ |
| ----------- | ------------- | ------------ | ---------- | --------- | ------------ |
| Adam        | 0.0001        | 0            | 68.86      | 90.48     | 10.63        |
| AdamW       | 0.0001        | 0.0001       | 67.62      | 91.84     | 8.07         |
| AdamW       | 0.0003        | 0.0001       | 69.50      | 92.52     | 12.98        |
| SGD         | 0.01          | 0.0005       | 67.67      | 90.14     | 14.27        |
| **AdaGrad** | **0.05**      | **0**        | **70.05**  | **93.54** | **7.74**     |

## Analysis

The experimental results show that different optimizer configurations lead to different detection performance.

Among the evaluated configurations, AdaGrad achieves the highest mIoU of 70.05% and Pd of 93.54%, together with the lowest Fa of 7.74 × 10⁻⁶.

These results provide experimental support for the adopted AdaGrad configuration under the evaluated training and testing conditions.

---

[Back to the supplementary materials overview](../)
