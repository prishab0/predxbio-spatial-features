# Spatial features of the NSCLC tumor microenvironment

TECBio REU 2026 at PredxBio / University of Pittsburgh. Author: Prisha Bhanushali.

`predxbio_spatial_features_PrishaBhanushali.ipynb` is an exploratory analysis of tumor and immune organisation in non-small cell lung cancer (NSCLC) H&E regions of interest.

## What the notebook does

1. Loads cell segmentation output and H&E images and builds per-cell features: area, eccentricity, darkness, entropy and local cell density.
2. Classifies annotated tissue regions as tumor or immune and measures tumor-to-immune distance per region.
3. Summarises each region and patient (395 regions from 82 patients), and compares features between histological subtypes.
4. Groups regions into immune architecture classes (hot, excluded, cold) and computes a composite architecture score.
5. Relates the features to overall survival with Cox proportional hazards models.

## Limits

* The survival analysis uses the **14 patients** who have both these features and linked TCGA outcome data (10 events). Seven univariate Cox models are reported without multiple-testing correction. The strongest result (tumor-to-immune distance, HR 0.31 per SD, 95% CI 0.14 to 0.72, p = 0.006) should be read as hypothesis-generating.
* The hazard ratios in the forest-plot cell are typed in from the printed Cox output above it, not recomputed in that cell.
* The architecture classes and score are defined from the same data they are then compared on; they are not validated on an independent cohort.

## Running it

Input data (segmentation JSON, H&E images, clinical tables) are not included. Place them in a local `data/` folder as the paths in the notebook expect, then run the cells top to bottom in one session.

```
pip install -r requirements.txt
```

The original notebook, including figure-polishing cells removed from this version, is in the repository history (commit 87932cc).
