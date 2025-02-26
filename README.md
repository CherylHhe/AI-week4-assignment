# GEOL0069 Week 4 Assignment: Unsupervised Classification of Radar Echoes

## Overview  
This repository addresses the classification of Sentinel-3 altimetry data into **sea ice** and **leads** using unsupervised learning. The workflow includes data preprocessing, feature extraction, Gaussian Mixture Model (GMM) clustering, visualization of results, and validation against ESA's ground truth labels. The project achieves **99% accuracy** in distinguishing sea ice from leads, demonstrating the efficacy of unsupervised methods for Earth Observation (EO) tasks.

---

## Repository Structure  
```
.
├── data/                    # Sentinel-3 NetCDF files (user-provided)
├── images/                  # Output plots (e.g., waveforms, scatter plots)
├── Chapter1_Unsupervised_Learning_Methods_Michel.ipynb  # Main Jupyter notebook
├── README.md                # This documentation
└── requirements.txt         # Python dependencies
```

---

## Installation  
1. **Clone the repository**:  
   ```bash
   git clone https://github.com/[your-username]/GEOL0069-Week4.git
   cd GEOL0069-Week4
   ```
2. **Install dependencies**:  
   ```bash
   pip install -r requirements.txt
   pip install netCDF4 rasterio scikit-learn matplotlib scipy
   ```
3. **Add data**:  
   - Place Sentinel-3 NetCDF files (e.g., `enhanced_measurement.nc`) in the `data/` directory.  
   - Update file paths in the notebook to match your local structure.  

---

## Methodology  
### Key Steps  
1. **Data Preprocessing**:  
   - Load and filter Sentinel-3 waveforms, latitude, longitude, and flags.  
   - Remove invalid data points (e.g., `lat >= -99999`).  

2. **Feature Extraction**:  
   - **Peakiness (PP)**: Quantifies waveform sharpness.  
   - **Signal Scattering Deviation (SSD)**: Measures waveform spread using Gaussian fitting.  

3. **Clustering**:  
   - Apply Gaussian Mixture Models (GMM) to classify echoes into sea ice (cluster 0) and leads (cluster 1).  
   - Standardize features (`sig_0`, `PP`, `SSD`) for optimal clustering performance.  

4. **Visualization**:  
   - Plot **mean waveforms** with standard deviation to compare sea ice and leads.  
   - Generate **scatter plots** of clustered data using feature pairs (`sig_0` vs. `PP`, `sig_0` vs. `SSD`).  
   - Align waveforms via cross-correlation to ensure temporal consistency.  

5. **Validation**:  
   - Compare GMM results with ESA’s official classification using a confusion matrix and classification report.  

---

## Results  
### 1. Confusion Matrix & Classification Report  
```
[[8856  22]  
 [  24 3293]]  

              precision  recall  f1-score   support  
      Sea Ice     1.00      1.00      1.00      8878  
        Lead      0.99      0.99      0.99      3317  
```  
**Accuracy**: 99%  

### 2. Key Observations  
- **Sea Ice**: Broader waveforms with higher variability in `SSD`.  
- **Leads**: Sharper peaks and lower feature spread.  

### 3. Visualization Examples  
- **Mean Waveforms**:  
  ![Mean Waveforms](images/mean_waveforms.png)  
- **Feature Scatter Plots**:  
  ![Scatter Plots](images/scatter_plots.png)  

---
