**Phase 2 – Model Training & Evaluation**

📖 **Overview**

Phase 2 focuses on training and evaluating a deep learning model to classify images as Real or Synthetic (AI-generated).
Using a pre-trained ResNet-18 architecture with transfer learning, we fine-tune the model on the CIFAKE dataset and evaluate its performance using multiple metrics.

🎯 **Objectives**

Load and preprocess CIFAKE dataset

Apply transfer learning using ResNet-18

Train model on Real vs Synthetic images

Evaluate performance using accuracy and classification metrics

Save trained model for Phase 3 analysis

🗂 **Dataset**

Dataset Used: CIFAKE (Real + Synthetic images)
Classes:
0 → Real
1 → Synthetic
Split Ratio:
Train: 70%
Validation: 15%
Test: 15%

🔄 **Workflow**

1️⃣ Data Preprocessing
Resize images (224×224)
Normalize using ImageNet mean & std
Convert to tensors
Create DataLoaders

2️⃣ Model Training
Freeze initial layers (optional)
Train for N epochs
Track:
Training Loss
Validation Loss
Validation Accuracy

3️⃣ Model Evaluation
Evaluate on Test Set
Generate:
Accuracy score
Confusion matrix
Classification report

4️⃣ Model Saving
Save trained model 

**Key Learnings
**
Transfer learning significantly improves performance.
ResNet-18 generalizes well for synthetic image detection.
Proper normalization and dataset splitting are crucial.
