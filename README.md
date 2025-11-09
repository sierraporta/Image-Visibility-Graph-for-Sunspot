# Image-Visibility-Graph-for-Sunspot
Image Visibility Graph (IVG) features from SDO/HMI daily images (2011–2025) to model the international sunspot number: reproducible pipeline de adquisición, preprocesado (máscara + limb darkening), extracción IVG (k=3,4), PCA y modelos (Ridge/Huber/GBR/RF/MLP).

# IVG–HMI: Visibility-graph features for daily sunspot modeling

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-orange.svg)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Data: SDO/HMI](https://img.shields.io/badge/Data-SDO%2FHMI-informational.svg)](https://sdo.gsfc.nasa.gov/)
[![Data: SILSO](https://img.shields.io/badge/Data-SILSO-informational.svg)](https://www.sidc.be/silso/)
[![DOI](https://img.shields.io/badge/DOI-tbd-lightgrey.svg)](#citation)

Reproducible pipeline that converts daily photospheric SDO/HMI images
(product `hmiigr_1024`, 12:00 UT) into **Image Visibility Graph (IVG)** descriptors
to study their relationship with the **international sunspot number (SSN)** from SILSO.
Includes on-the-fly acquisition, disk masking, optional limb-darkening flattening,
patchwise IVG (k=3,4), normalization/Hellinger, PCA (64/128/256), and a suite of
linear/non-linear models (Ridge, Huber, Gradient Boosting, Random Forest, MLP).

---

## 🔎 Method at a glance
- **Robust disk mask** (low threshold; center/radius via 99th-percentile distances).
- **Optional limb darkening flattening** (2-D polynomial fit, degree 4).
- **Patchwise IVG**: row/column/diagonal tests → bit pattern → label histogram `Z_k`.
- **Normalization** (L1 + optional Hellinger) and **moderate PCA** (64–256).
- **Models** with stratified random split and metrics (MAE, RMSE, R², Spearman ρ).

---

