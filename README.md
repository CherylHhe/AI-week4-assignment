# GEOL0069 Week 4 Assignment: Unsupervised Learning for Sea Ice and Lead Classification

## Overview
This repository contains code and documentation for classifying radar echoes into **sea ice** and **leads** using unsupervised learning methods. The workflow includes:
- **Data preprocessing** for Sentinel-3 altimetry data.
- **Feature extraction** (e.g., peakiness, waveform parameters).
- **Clustering** using Gaussian Mixture Models (GMM) and K-means.
- **Visualization** of clustered data, average echo shapes, and uncertainty.
- **Validation** against ESA's official classification using a confusion matrix.

## Repository Structure

## Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/[your-username]/GEOL0069-Week4.git
   cd GEOL0069-Week4

   pip install -r requirements.txt
# Additional installations for handling NetCDF and raster data:
pip install netCDF4 rasterio scikit-learn matplotlib scipy

jupyter notebook Chapter1_Unsupervised_Learning_Methods_Michel.ipynb (This is the first file provided by our Lecturer Michel, the second one I made some changes: deleted the plots showing all the echos)

Confusion Matrix:
[[8856  22]
 [  24 3293]]

Classification Report:
              precision  recall  f1-score   support
         0.0       1.00      1.00      1.00      8878
         1.0       0.99      0.99      0.99      3317
