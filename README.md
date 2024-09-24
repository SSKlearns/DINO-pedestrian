# Fine-tuning DINO Model for Pedestrian Detection

## Project Overview
This project involves fine-tuning the DINO model for pedestrian detection using a dataset featuring individuals walking around the IIT Delhi campus. The model was trained and evaluated using various cloud platforms due to the large computational resource requirements.

## Experiments and Approach
### 1. Dataset Preparation
- The dataset consists of 199 images and corresponding bounding boxes provided in COCO format.
- The dataset was split into an 80:20 ratio for training and validation.
- PyTorch's `DataLoader` was used to shuffle and split the dataset, and separate annotation files and image directories were created for both the training and validation sets.

### 2. DINO Model Setup
- The DINO model with a ResNet-50 backbone pre-trained for 33 epochs was used as the base model.
- The official DINO repository was cloned, and dependencies were installed via `requirements.txt`.
- The configuration for the model was modified in `DINO_4scale.py` to adjust parameters like `num_classes` for pedestrian detection.
- Remeber to follow the instructions to setup DINO from the <a href="https://github.com/IDEA-Research/DINO">official repository</a>.
  
### 3. Fine-tuning the Model
- Fine-tuning was conducted by freezing the backbone layers and training only the top layers.
- Initially, challenges arose with the fine-tuning, leading to poor evaluation metrics. Freezing the base layers helped resolve these issues.
- The final fine-tuned model produced satisfactory results.
- Link to Fine-tuned weights: https://drive.google.com/file/d/1X6M3FghNh8XQmn86COwJzzYxSk12vr-9/view?usp=sharing

### 4. Computational Challenges
- **Local Setup**: The local machine lacked the required resources to train the model effectively.
- **Google Colab**: Used as a cloud solution, but rate limiting caused interruptions during training.
- **Kaggle**: Provided a stable environment, though GPU time was limited.
- **Precautions**: To mitigate the risk of interruptions, training progress was monitored using the Weights and Biases (WandB) library.

## Results
### Evaluation Metrics for Pre-trained Model
| Metric | IoU = 0.50:0.95 (all) | IoU = 0.50 (all) | IoU = 0.75 (all) |
|--------|-----------------------|------------------|------------------|
| AP     | 0.508                 | 0.860            | 0.570            |

### Evaluation Metrics for Fine-tuned Model
| Metric | IoU = 0.50:0.95 (all) | IoU = 0.50 (all) | IoU = 0.75 (all) |
|--------|-----------------------|------------------|------------------|
| AP     | 0.326                 | 0.648            | 0.283            |

The fine-tuned model showed a performance decrease compared to the pre-trained model but achieved satisfactory results considering the computational constraints.
