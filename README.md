# BCSCENet: Supplementary Materials

*Experimental results and analyses for infrared small target detection*

<p align="center"><img src="assets/readme_accent.svg" alt="" width="100%"></p>

**Background Clutter Suppression and Contrast Enhancement Network for Infrared Small Target Detection**

*IEEE Transactions on Geoscience and Remote Sensing (TGRS)*

---

## Overview

This repository contains supplementary experimental results and analyses for BCSCENet, a background clutter suppression and contrast enhancement network for infrared small target detection (IRSTD).

BCSCENet incorporates three task-oriented modules: Differentiable Planar Background Suppression (DPBS), Structure Tensor Anisotropy Gate (STAG), and Local Contrast Residual Enhancement (LCRE). These modules are designed to suppress smooth background trends, reduce structured interference, and enhance local target–background feature differences, respectively.

The supplementary materials cover component ablations, qualitative comparisons, loss function evaluation, background clutter analysis, STAG placement and orientation analysis, cross-dataset evaluation, and optimizer comparison.

## Supplementary Experiments

| Experiment                         | Description                                                                       |
| ---------------------------------- | --------------------------------------------------------------------------------- |
| [CARAFE Ablation](CARAFE_Ablation/) | Performance analysis of CARAFE and DPBS configurations. |
| [Additional Qualitative Comparisons](Additional_Qualitative_Comparisons/) | Qualitative comparison on additional infrared test scenes. |
| [Loss Function Ablation](Loss_Function_Ablation/) | Evaluation of different loss functions and combinations. |
| [Background Clutter Analysis](Background_Clutter_Analysis/) | Background classification, distribution statistics, and module response analysis. |
| [STAG Placement Ablation](STAG_Placement_Ablation/) | Comparison of STAG placement across decoder stages. |
| [Cross-Dataset Evaluation](Cross_Dataset_Evaluation/) | Bidirectional evaluation between IRSTD-1K and NUAA-SIRST. |
| [STAG Orientation Analysis](STAG_Orientation_Analysis/) | Evaluation under different structured-clutter orientations. |
| [CARAFE–DPBS Interaction](CARAFE_DPBS_Interaction/) | Analysis of the combined effects of CARAFE and DPBS. |
| [Optimizer Comparison](Optimizer_Comparison/) | Comparison of different optimizer configurations. |

## Evaluation Metrics

The experimental results are reported using three metrics:

- **mIoU (%):** Mean Intersection over Union.
- **Pd (%):** Probability of Detection.
- **Fa (×10⁻⁶):** False Alarm Rate.

Higher mIoU and Pd values indicate better performance, whereas lower Fa values indicate fewer false alarms.

## Experimental Datasets

The experiments include the public IRSTD-1K and NUAA-SIRST datasets. Individual experiment sections specify the corresponding evaluation datasets and configurations.

## Organization

Each directory presents a specific experimental analysis, including the relevant configurations, quantitative results, and findings. Representative visualizations and sample information are included for experiments involving qualitative comparisons or background subset analysis.

This repository contains experimental materials only. Model source code, training code, model configurations, and model weights are not included.
