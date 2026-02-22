# Phase 2 – Adversarial Modification & Evasion Analysis

## Overview

Phase 2 focuses on exploring **adversarial modifications and evasion** for a synthetic image detector built in Phase 1.  
The goal is to understand how synthetic images can be minimally modified to reduce the detector's confidence or flip its prediction to "real," while still remaining visually realistic.

All experiments in this phase are **inference-based** using the **pre-trained ResNet-18 model** checkpoint from Phase 1. No new model training was performed.

## Dataset

- **CIFAKE dataset** (Real + Synthetic images)  
- Classes:  
  - `0` → Real  
  - `1` → Synthetic  
- Phase 2 primarily uses **synthetic test samples** for evasion experiments  
- Metadata CSV: `metadata.csv`  

## Workflow

### 1️⃣ High-Confidence Synthetic Sample Selection

- Identify synthetic images from the test set that the detector classifies as fake with **high confidence**  
- These images form the base for evasion experiments  

### 2️⃣ Adversarial / Evasion Modifications

- Iteratively modify the selected images to reduce model confidence or flip prediction:  
  - **Pixel-level perturbations**: Gaussian blur, Gaussian noise, brightness adjustments  
  - **Frequency-domain manipulations**: high/low-pass filtering, masking specific frequency bands  
  - **Combination manipulations**: Pixel + frequency modifications applied sequentially  
- Track **model confidence (`p_fake`)** at each step  
- Save intermediate modified images to visualize the **original → modified → final evading image** sequence  

### 3️⃣ Analysis

- Analyze why the evasion worked:  
  - Which features or frequencies were suppressed or shifted  
  - How minimal changes can cause significant drops in confidence  
- Generate plots for confidence progression across modification stages  

### 4️⃣ Output

- CSV files:  
  - `pixel_confidence_progression.csv` – confidence scores for pixel-level modifications  
  - `freq_confidence_progression.csv` – confidence scores for frequency-domain manipulations  
  - `summary_stats.csv` – statistical summaries (mean, SEM) of confidence changes  
- Visualizations:  
  - Original vs modified images  
  - Confidence progression plots  
  - Frequency spectra of manipulated images  

## Key Learnings

- **Minimal, targeted modifications** can significantly reduce detector confidence while keeping images visually realistic  
- Pixel-level and frequency-level manipulations reveal which features the model relies on  
- Iterative evasion experiments help in understanding model vulnerabilities and robustness  

## Notes

- Phase 2 **does not include training**; all modifications are applied to pre-trained models in inference mode  
- Focus is on analysis and understanding of model sensitivity, rather than on achieving perfect evasion  
