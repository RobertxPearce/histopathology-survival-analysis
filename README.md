# Uncertainty-Aware Histopathology Survival Analysis

## Pipeline

```mermaid
flowchart TD
    A["① Data Preparation\nSVS slides + BCR XML\ndownload from GDC Portal"]
    B["② Preprocessing — Trident\nSegmentation → Patching → Feature Extraction\nUNI / CONCH Foundation Models"]
    C["③ MIL Model — Patches → Slide Representation\nABMIL / CLAM / TransMIL / HipoMap\nN patches → 1 slide vector 512-dim"]
    D["④ Survival Training\nCox Loss + SurvRNC Loss + SNGP Uncertainty"]
    E["⑤ Evaluation and Visualization\nC-index / Kaplan-Meier / Attention Heatmap"]

    A --> B --> C --> D --> E

    style A fill:#f5f0eb,stroke:#999
    style B fill:#e8f5f5,stroke:#6bc
    style C fill:#ede8f5,stroke:#96c
    style D fill:#fdecea,stroke:#e88
    style E fill:#eaf5ea,stroke:#6a6
```

## Datasets
- The Cancer Genome Atlas Program (TCGA) Lung Adenocarcinoma (LUAD)
    - Data Source: [National Cancer Institute GDC Data Portal](https://portal.gdc.cancer.gov/)
    - Manifest: [gdc_manifest_full_luad_dx.txt](manifests/gdc_manifest_full_luad_dx.txt)
    - Result: 478 cases, 541 files (some cases have multiple diagnostic slides)

    | Filter                | Value            |
    |------------------------|------------------|
    | Program               | TCGA             |
    | Project               | TCGA-LUAD        |
    | Access                | Open             |
    | Data Format           | svs              |
    | Data Type             | Slide Image      |
    | Experimental Strategy | Diagnostic Slide |

## Contributors
| Name                 | University                             |
|----------------------| -------------------------------------- |
| Robert Pearce        | University of Nevada, Las Vegas        |
| Sejun Park           | Gyeonggi Science Technology University |
| Hailey (Heejae Kwon) | Sookmyung Womens University           |
| HyeonKyeong Lee      | Gyeongsang National University         |

## Acknowledgments
This project was completed during the International Machine Learning Camp hosted by the [University of Nevada, Las Vegas](https://www.unlv.edu/cs). Resources and guidance were provided by [Dr. Mingon Kang](https://kang.dataxlab.org/index.php).
