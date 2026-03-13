# Transfer Learning with EfficientNet (Food-11 Classification)

## Project Overview

This project applies **Transfer Learning** using the **EfficientNetB0** architecture to classify images from the **Food-11 dataset**.  
Two different approaches were evaluated:

1. **Feature Extraction**
2. **Fine-Tuning**

The experiments were implemented using **TensorFlow / Keras** and executed in **Google Colab with GPU support**.

---

# Model Information

Model Architecture: EfficientNetB0  
Input Size: 224 × 224  
Framework: TensorFlow / Keras  
Optimizer: Adam  
Loss Function: Sparse Categorical Crossentropy  
Number of Classes: 11  

---

# Experiments

## 1. Feature Extraction

In this approach, the pretrained EfficientNetB0 model was used as a fixed feature extractor.

- All base model layers were **frozen**
- Only the **classification head** was trained

### Results

Test Accuracy: **~0.89 (89%)**  
Test Loss: **~0.33**

This approach performed very well since the pretrained EfficientNet features already captured useful visual representations.

---

## 2. Fine-Tuning

In the fine-tuning experiment:

- The last layers of the EfficientNet model were **unfrozen**
- The model was retrained with a **lower learning rate**

### Results

Test Accuracy: **~0.85 (85%)**  
Test Loss: **~0.48**

Fine-tuning allowed the network to slightly adapt to the dataset, although the performance was slightly lower than the feature extraction approach in this case.

---

# Comparison

| Method | Test Accuracy |
|------|------|
Feature Extraction | **~89%** |
Fine-Tuning | **~85%** |

Feature extraction achieved better performance on this dataset.  
This indicates that the pretrained EfficientNet features were already well suited for the Food-11 classification task.

---

# Training Metrics

During training, the following metrics were monitored:

- Training Accuracy
- Validation Accuracy
- Training Loss
- Validation Loss

The plots below illustrate the training progress.

## Feature Extraction Training

Accuracy and loss curves show stable learning behavior.

## Fine-Tuning Training

Fine-tuning also demonstrated stable convergence with slightly different training dynamics.

---

# Observations

## Generalization

Training and validation curves were close to each other, indicating that the model generalized well to unseen data.

## Convergence

Both training loss and validation loss decreased during training, showing that the optimization process converged properly.

## Overfitting

No significant overfitting was observed since validation performance remained stable and close to training performance.

---

# Bonus – Experiment Tracking

To improve experiment reproducibility, **MLflow** was integrated with **DagsHub**.

The following experiment information was tracked:

- Experiment runs
- Model parameters
- Evaluation metrics
- Model artifacts
- Training outputs

Each experiment run was logged and visualized using **DagsHub Experiments**.

This setup allows easier comparison between experiments and better experiment management.

---

# Tools and Technologies

- Python
- TensorFlow / Keras
- EfficientNet
- Google Colab (GPU)
- MLflow
- DagsHub

---

# Conclusion

Transfer learning using EfficientNetB0 proved effective for the Food-11 classification task.

Feature extraction achieved the best performance, demonstrating that pretrained features can provide strong results even with minimal retraining.

Experiment tracking with MLflow and DagsHub further improved the reproducibility and organization of the project.