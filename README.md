# EY Open Science AI Data Challenge 2025 - Final Submission

## Team
- **Ton That Nhat Minh (minhtonthatnhat@gmail.com)**  
- **Tran Hai Duong**  
- **Truong Hao Nhien**  

## Challenge Overview
This repository contains our final submission for the [EY Open Science AI and Data Challenge 2025](https://challenge.ey.com/challenges/the-2025-ey-open-science-ai-and-data-challenge-cooling-urban-heat-islands-external-participants).  

### Final Ranking:
- **Rank:** 185 / 380 teams  
- **R² Score:** 0.8345  
- We successfully passed the **0.8 R²** threshold required by the organizers to receive a participation certificate.  

## Repository Contents
This repository includes both the original challenge-provided files and our own implementation files.

### Folder Structure:
```
📂 EY_Challenge_2025
│── 📄 2025 EY Open Science AI Data Challenge.pdf  # Challenge details  
│── 🌍 Building_Footprint.kml                      # KML file for building footprints  
│── 📜 Landsat_LST.ipynb                           # Notebook for processing Landsat LST data  
│── 📜 model.ipynb                                 # Notebook for model testing  
│── 📊 NY_Mesonet_Weather.xlsx                     # Weather data from NY Mesonet  
│── 📄 README.md                                   # This README file  
│── 📜 Sentinel2_GeoTIFF.ipynb                     # Notebook to process Sentinel-2 GeoTIFF images  
│── 📜 Submission_template_UHI2025-v2.csv          # Submission template for challenge  
│── 📜 Training_data_uhi_index_UHI2025-v2.csv      # Training dataset for UHI index  
│── 📜 UHI Experiment Sample Benchmark Notebook.ipynb  # Sample notebook for UHI experiment  
```

## Approach
Our approach takes inspiration from the sample notebook provided by the organizers: **UHI Experiment Sample Benchmark Notebook V5.ipynb**.

### Steps:
1. **Generate a TIFF image** from Sentinel 2 dataset capturing multispectral bands over New York for the targeted date: **July 24, 2021**.
2. **Compute indices** from the bands, including:
   - Normalized Difference Vegetation Index (**NDVI**)
   - Normalized Difference Built-up Index (**NDBI**)
   - Enhanced Vegetation Index (**EVI**)
   - Normalized Difference Water Index (**NDWI**)
   - Fractional Vegetation Cover (**FVC**)
   - Emissivity (**E**)
3. **Apply spatial convolution** on **NDVI** and **NDBI** indices to enhance spatial feature extraction.
4. **Train a model using AutoGluon**:
   - **Configuration:** `best_quality` training mode
   - **Training time limit:** `3600` seconds (1 hour)

## Experiment Results
Through multiple index combinations, we observed the following performance:

- Using bands **'B01', 'B06', 'B11', 'NDVI', 'NDWI'**, we achieved an **R² score of 0.83**.
- By adding **NDVI_convoluted** and **NDWI_convoluted** to the above features, the **R² score improved to 0.8345**.

## How to replicate our result
Follow these steps to process data, train the model, and generate predictions:

1. **Run `Sentinel2_GeoTIFF.ipynb`**  
   - This script processes Sentinel-2 data and generates a TIFF image for the target date.  

2. **Run `main.ipynb`**   
   - This notebook handles data loading, model training, prediction, and generates the final submission CSV.  

---

Feel free to reach out if you have any questions or improvements! 🚀