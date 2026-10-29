# Pulmonary Risk Assessment and Scoliosis Severity Classification

## Overview

This project presents a multi-modal deep learning framework for automated scoliosis severity classification and preliminary pulmonary-risk assessment using spinal X-ray images. It combines deep image representations with spinal geometric features to classify cases into three categories: Healthy, Mild, and Significant.

The system integrates image preprocessing, body-region segmentation, automated spinal centerline detection, geometric feature extraction, and ensemble learning to support research-oriented medical image analysis.

## Key Features

- **X-ray Preprocessing:** Image resizing, polarity correction, and contrast enhancement using CLAHE.
- **Body Segmentation:** Identifies the relevant body region for focused spinal analysis.
- **Spinal Centerline Detection:** Estimates the spinal trajectory using ridge evidence and dynamic programming.
- **Geometric Feature Extraction:** Extracts spinal curvature approximations, lateral deviation, apex position, chest asymmetry, and tilt-related features.
- **Deep Feature Extraction:** Uses ImageNet-pretrained EfficientNet-B0 to learn representative features from X-ray images.
- **Multi-Modal Feature Fusion:** Combines deep image features with numerical spinal geometry features.
- **Ensemble Classification:** Uses five-fold stratified cross-validation and ensemble predictions for three-class severity classification.
- **Pulmonary-Risk Scoring:** Generates a preliminary severity-weighted score from the predicted class probabilities.

## Technologies Used

- Python
- PyTorch
- EfficientNet-B0
- OpenCV
- NumPy
- Scikit-learn
- Matplotlib

## Model Architecture

The framework follows a multi-stage pipeline:

1. Input spinal X-ray image.
2. Image preprocessing and body-region segmentation.
3. Automated spinal centerline detection.
4. Extraction of nine numerical geometric and detection features.
5. EfficientNet-B0 extraction of a 1,280-dimensional image representation.
6. Fusion with a 32-dimensional numerical feature representation.
7. Five-fold ensemble classification into Healthy, Mild, or Significant.
8. Preliminary pulmonary-risk score computation.

## Experimental Results

The model was evaluated on 338 held-out X-ray images.

| Evaluation Metric | Performance |
|---|---:|
| Three-class ensemble accuracy | 86.7% |
| Macro-F1 score | 85.7% |
| Accuracy with test-time augmentation | 87.0% |
| Accuracy with expected-severity decoding | 87.9% |
| Binary scoliosis screening accuracy | 93.8% |
| Binary screening sensitivity | 93.7% |
| Binary screening specificity | 94.4% |

The model-derived mean risk scores increased with severity: 0.038 for Healthy, 0.396 for Mild, and 0.789 for Significant cases.

## Project Structure

```text
Pulmonary-Risk-Scoliosis-Classification/
├── Pulmonary_Risk_Scoliosis_3Class_Ensemble.ipynb
├── Pulmonary_UI/
└── README.md
```

## Getting Started

1. Clone or download this repository.
2. Open the notebook in Google Colab or Jupyter Notebook.
3. Install the required Python dependencies.
4. Configure the dataset and model paths according to your environment.
5. Execute the notebook cells to run preprocessing, training, evaluation, and inference.

Dataset files and trained model checkpoints may need to be obtained or configured separately.

## Limitations and Future Work

The spinal centerline and derived curvature measurements are approximations and are not equivalent to clinical Cobb-angle measurements. The pulmonary-risk score uses predefined severity weights and has not been validated against pulmonary-function measurements. Further work requires external dataset evaluation, integration of clinical variables, and clinical validation.

## Disclaimer

This project is intended for academic research and experimentation. The pulmonary-risk score is a preliminary model-derived indicator, not a clinically validated risk probability or medical diagnosis. The system must not replace professional medical assessment or pulmonary-function testing.
