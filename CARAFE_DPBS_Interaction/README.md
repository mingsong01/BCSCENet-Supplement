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

The performance degradation observed when CARAFE is used alone may be related to insufficient suppression of background interference in the input features. Based on the local content of the input features, CARAFE generates a corresponding reassembly kernel for each upsampling location and uses these kernels to perform weighted aggregation of neighboring features [1]. When strong background interference is present in the input features, the associated background features may also participate in the upsampling process, affecting the distinction between small targets and their surrounding background. Because infrared small targets typically occupy only a small number of pixels, this effect may lead to prediction deviations in target regions or false detections in the background, thereby affecting model performance.

DPBS models and suppresses smooth background trends before upsampling, thereby reducing the influence of background interference on subsequent feature reassembly. Previous studies have also shown that detail recovery and boundary preservation during feature upsampling can affect dense prediction results [2], [3], providing related support for this interpretation.

## References

[1] J. Wang, K. Chen, R. Xu, Z. Liu, C. C. Loy, and D. Lin, “[CARAFE: Content-Aware ReAssembly of FEatures](https://openaccess.thecvf.com/content_ICCV_2019/html/Wang_CARAFE_Content-Aware_ReAssembly_of_FEatures_ICCV_2019_paper.html),” in *Proc. IEEE/CVF Int. Conf. Comput. Vis. (ICCV)*, 2019, pp. 3007–3016.

[2] H. Lu, W. Liu, H. Fu, and Z. Cao, “[FADE: Fusing the Assets of Decoder and Encoder for Task-Agnostic Upsampling](https://doi.org/10.1007/978-3-031-19812-0_14),” in *Proc. Eur. Conf. Comput. Vis. (ECCV)*, 2022, pp. 214–230, doi: 10.1007/978-3-031-19812-0_14.

[3] H. Lu, W. Liu, Z. Ye, H. Fu, Y. Liu, and Z. Cao, “[SAPA: Similarity-Aware Point Affiliation for Feature Upsampling](https://proceedings.neurips.cc/paper_files/paper/2022/hash/83ccb398f3ce9c4d137011f36a03c7d4-Abstract-Conference.html),” in *Advances in Neural Information Processing Systems*, vol. 35, pp. 20889–20901, 2022, doi: 10.52202/068431-1519.

---

[Back to the supplementary materials overview](../)
