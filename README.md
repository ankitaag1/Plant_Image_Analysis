# Plant_Image_Analysis

This notebook extracts handcrafted image features from **multi-view plant images** captured under **normal** and **moisture stress** conditions.  
Each plant is treated as a single biological sample and is represented by **three image views** to capture structural and visual variability.

## Image Acquisition and Organization

For each plant, **three different image views** are available:
- **Side view** – captures leaf posture and height
- **Top view** – captures canopy spread and density
- **Angled view** – captures intermediate structural characteristics

Images are organized using the following directory structure:

dataset/
│
├── normal/
│ ├── plant_01/
│ │ ├── side.jpg
│ │ ├── top.jpg
│ │ └── angle.jpg
│ ├── plant_02/
│ │ └── ...
│
└── stress/
├── plant_01/
│ ├── side.jpg
│ ├── top.jpg
│ └── angle.jpg
└── plant_02/
└── ...


Each **plant folder corresponds to one plant sample**, and all images within a folder belong to the same plant captured from different perspectives.

## Feature Extraction and Aggregation

Handcrafted features are extracted **independently from each image**, including:
- Color features (RGB, HSV, Excess Green)
- Texture features (GLCM, LBP)
- Shape features (area, perimeter, aspect ratio, solidity)

To obtain a **plant-level representation**, features are aggregated across the three views using:
- Mean across views
- Standard deviation across views

This results in a **single feature vector per plant**, ensuring robustness to viewpoint variation.

## Machine Learning Models Evaluated

The following classical machine learning models are trained and evaluated:
- **Support Vector Machine (SVM)**
- **Logistic Regression**
- **k-Nearest Neighbors (k = 3)**
- **Random Forest ( n= 1000)**

## Evaluation Metrics

Model performance is assessed using:
- **Precision**
- **Recall**
- **F1-score**

The best-performing model is selected based on **F1-score**.

## Feature Selection and Interpretability

To identify the most discriminative features for moisture stress detection:
- **Permutation Feature Importance** is applied to the best-performing model
- The **top 20 most important features** are reported and analyzed

This approach enables biologically interpretable insights into stress-related changes in plant color, texture, and morphology.

