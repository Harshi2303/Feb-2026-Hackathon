# Phase 2 – Model Training & Evaluation

## Overview
Phase 2 focuses on training and evaluating a deep learning model to classify images as Real or Synthetic (AI-generated).  
We use a pre-trained **ResNet-18** architecture with transfer learning and fine-tune the model on the CIFAKE dataset.

## Objectives
- Load and preprocess the CIFAKE dataset
- Apply transfer learning using ResNet-18
- Train the model on Real vs Synthetic images
- Evaluate performance using accuracy and classification metrics
- Save the trained model for Phase 3 analysis

## Dataset
**Dataset Used:** CIFAKE (Real + Synthetic images)  

**Classes:**
- 0 → Real
- 1 → Synthetic

**Split Ratio:**
- Train: 70%
- Validation: 15%
- Test: 15%

## Workflow

### 1. Data Preprocessing
- Resize images to 224×224
- Normalize using ImageNet mean & standard deviation
- Convert images to tensors
- Create DataLoaders for train, validation, and test sets

### 2. Model Training
- Use pre-trained ResNet-18
- Replace the final fully connected layer for binary classification
- Train the model for N epochs
- Track:
  - Training Loss
  - Validation Accuracy

### 3. Model Evaluation
- Evaluate the trained model on the test set
- Generate:
  - Accuracy score
  - Confusion matrix *(if implemented)*
  - Classification report *(if implemented)*

### 4. Model Saving
- Save the trained model for future use:
```python
torch.save(model.state_dict(), "resnet18_phase2.pth")
