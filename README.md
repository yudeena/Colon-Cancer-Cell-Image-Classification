
## Project Objectives

- **Binary classification**: Predict whether a colon cell is cancerous or non-cancerous.
- **Multiclass classification**: Classify colon cells into one of four types: epithelial, fibroblast, inflammatory, or others.

## Dataset

Modified from the **CRCHistoPhenotypes** dataset. Includes ~20,000 27×27 RGB images of individual colon cells from 99 patients, with two corresponding label files:

- `data_labels_mainData.csv` (~9,900 images): Labeled with `isCancerous` and `cellTypeName`
- `data_labels_extraData.csv` (~10,000 images): Labeled only with `isCancerous`

## Methods and Models

### Exploratory Data Analysis
- Identified class imbalances and visual artifacts
- Sampled and visualized each class
- Highlighted image quality issues (blur, occlusion)

### Preprocessing
- Image resizing and normalization ([0, 1] range)
- One-hot encoding for multiclass labels
- Targeted augmentation for underrepresented classes

### Models

**Binary Classification Models**
- `B-Base`: Simple MLP
- `B-02`: CNN with max pooling, class weighting (final selection)
- `B-03`: CNN with BatchNorm, early stopping

**Multiclass Classification Models**
- `M-Base`: 3-layer CNN
- `M-01`: CNN with L2 regularisation, dropout (final selection)

### Evaluation

- **Split**: Stratified 60/20/20 (Train/Validation/Test)
- **Metrics**: F1-score (weighted), AUC-ROC, Confusion Matrices
- **Visualization**: Learning curves, ROC curves, confusion matrices

### Independent Evaluation

- Benchmarked against published results:
  - Sirinukunwattana et al. (2016)
  - Alom et al. (2022)
  - Kavitha et al. (2022)

- Applied a critical lens to class imbalance, image resolution, and lack of transfer learning.

- Discussed the use of semi-supervised learning using the unlabeled `extraData` subset to improve cancer classification.

## Final Judgement

| Task                | Final Model | Test F1 | Notes |
|---------------------|-------------|---------|-------|
| isCancerous         | B-02        | 0.891   | Stable learning, robust generalization |
| cellTypeName        | M-01        | 0.763   | Best performance with regularisation |

## Authors

- **Deena Yu-Fawcett** – *s3925523*
- **Josh Cavallin** – *s3886768*
