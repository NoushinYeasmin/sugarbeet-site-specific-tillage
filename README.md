# Drone-Based Weed Detection & GIS Prescription Mapping for Site-Specific Tillage (SST)

An end-to-end geospatial and machine learning workflow for detecting inter-row and intra-row weeds from high-resolution UAV orthomosaics and generating GIS-ready prescription zones for site-specific mechanical cultivation in sugar beet fields.

## Project Workflow
1. **Vegetation Segmentation & Row Geometry:** Extracts vegetation indices and estimates crop row orientation and spacing.
2. **Spatial Hold-Out Machine Learning:** Trains a Random Forest classifier across multiple fields (`000`, `001`, `002`, `004`) and evaluates generalization on a completely unseen field (`003`).
3. **GIS Prescription Map Generation:** Aggregates pixel-level weed predictions into spatial management grids (`skip`, `low`, `high` cultivation zones) exported in GeoJSON format.
4. **Agronomic & Accuracy Evaluation:** Computes pixel-level and zone-level accuracy metrics alongside estimated cultivated area savings compared to whole-field tillage.

## Dataset & Context
- **Dataset:** [WeedMap (ETH Zurich)](https://doi.org/10.3929/ethz-c-000788571) — High-resolution (~1 cm GSD) UAV orthomosaics with pixel-level expert crop/weed annotations from sugar beet fields in Rheinbach (Germany) and Eschikon (Switzerland) (Sa et al., 2018).
- **Note on Geographic Scope:** This benchmark evaluation uses European sugar beet UAV imagery to validate the end-to-end SST mapping pipeline prior to adaptation on North Dakota field datasets.

## Key Outputs (Held-Out Field `003`)
- **Visual Summary:** `results/field_003/summary_003.png` (Orthomosaic, expert ground truth, model predictions, and prescription zones)
- **Feature Importance:** `results/field_003/feature_importance.png`
- **Prescription Zones:** `results/field_003/prescription_003.geojson`
- **Evaluation Metrics:** `results/field_003/metrics.json` & `results/field_003/pixel_metrics.csv`

![Summary Output](results/field_003/summary_003.png)

## Tools & Libraries
Python, Google Colab, Scikit-Learn, Rasterio, GeoPandas, NumPy, Matplotlib
