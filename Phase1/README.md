# Phase 1 – Synthetic Image Detection

## Project Overview
This project focuses on detecting synthetic (AI-generated) images using deep learning. Phase 1 includes preparing the dataset, training the model, evaluating performance, and generating explainable visualizations.

---

## Folder Structure
Phase1/
├── data/                 # CIFAKE dataset, preprocessed images
├── M1_Phase1.ipynb       # Model training notebook
├── M2_Phase1.ipynb       # Data preprocessing & augmentation notebook
├── M3_Phase1.ipynb       # Metrics & explainability notebook
├── models/               # Saved model checkpoints
├── results_metrics/      # Metrics tables and plots
├── results_gradcam/      # Grad-CAM / saliency images
└── README.md             # Project documentation

---

## Quick Start

1. Open the notebooks in order:
   - `M2_Phase1.ipynb` → Preprocess and augment dataset  
   - `M1_Phase1.ipynb` → Train the detection model  
   - `M3_Phase1.ipynb` → Evaluate model and generate Grad-CAM visualizations  

2. Follow the instructions inside each notebook to run the full workflow.

---

## Dependencies

- Python 3.10+  
- PyTorch / TensorFlow (depending on chosen model)  
- OpenCV, NumPy, Pandas, Matplotlib, Seaborn  
- Any other libraries listed at the top of each notebook  

---

## Outputs

- **Model checkpoints:** `/models/`  
- **Metrics tables and plots:** `/results_metrics/`  
- **Grad-CAM / saliency images:** `/results_gradcam/`

