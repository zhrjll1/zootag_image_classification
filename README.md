# ZooTag – Animal Image Classification

ZooTag is a collaborative AI and Machine Learning course project focused on classifying animal images into seven categories using deep learning and transfer learning.

The project covers an end-to-end machine learning workflow, from data preprocessing and augmentation to model training, fine-tuning, evaluation, and conversion to TensorFlow Lite for more lightweight inference.

## Project Overview

The goal of ZooTag was to build an image classification model capable of recognizing broad animal categories from images.

The model classifies images into seven classes:

- Amphibian
- Bird
- Fish
- Insect
- Mammal
- Marine invertebrate
- Reptile

The dataset used in the project contained approximately 1,220 animal images.

## Approach

The project used **MobileNetV2**, pretrained on ImageNet, as the backbone of the classification model.

Because the dataset was relatively small, transfer learning was used instead of training a deep neural network from scratch.

The workflow included:

1. Preparing and splitting the dataset into training, validation, and test sets
2. Resizing images to 224 × 224 pixels
3. Applying image augmentation
4. Using pretrained MobileNetV2 for feature extraction
5. Training a new classification head
6. Fine-tuning selected MobileNetV2 layers
7. Evaluating the model using multiple classification metrics
8. Converting the trained model to TensorFlow Lite
9. Testing lightweight inference using the TensorFlow Lite interpreter

## Data Preprocessing and Augmentation

Images were resized to **224 × 224 pixels**.

Training data augmentation included:

- Random horizontal flipping
- Random contrast adjustment

These techniques were used to introduce additional variation into the training data and improve generalization. 

## Transfer Learning

The project used MobileNetV2 pretrained on ImageNet.

Training was carried out in two stages.

## Stage 1 – Feature Extraction

The pretrained MobileNetV2 layers were initially frozen.

A new classification head was trained on top of the pretrained network for the seven animal categories.

The classification head included:

- Global Average Pooling
- Dropout
- Dense output layer
- Softmax activation

## Stage 2 – Fine-Tuning

After the initial training stage, part of the MobileNetV2 network was unfrozen.

Approximately the final 21 layers were fine-tuned using a lower learning rate.

This allowed higher-level pretrained features to adapt more specifically to the ZooTag classification task.

Early stopping was also used during training to reduce unnecessary training and help control overfitting.

## Model Evaluation

The model was evaluated using several metrics rather than relying only on accuracy.

Evaluation included:

- Accuracy
- Precision
- Recall
- F1 score
- Confusion matrix
- Classification report

The final model achieved approximately:
| Metric            | Result |
| ----------------- | -----: |
| Test Accuracy     | ~85.9% |
| Weighted F1 Score | ~0.857 |
| Test Images       |    128 |

The confusion matrix and classification report were used to examine performance across individual animal categories.

Some categories were easier for the model to distinguish than others. Insects performed particularly well, while reptiles and marine invertebrates were more challenging.

## TensorFlow Lite Optimization

After training and evaluating the Keras model, the model was converted to TensorFlow Lite.

The conversion used TensorFlow Lite optimization with float16 weights to reduce model size while maintaining useful prediction performance.

The TensorFlow Lite interpreter was then used to perform predictions on sample images.

Predictions from the lightweight model were compared with the original Keras model to verify that the converted model continued to produce meaningful results.

This stage introduced deployment-oriented considerations such as:

- Model size
- Inference efficiency
- Lightweight execution
- Resource-constrained environments
- Edge AI applications

## Technologies
## Machine Learning
- TensorFlow
- Keras
- MobileNetV2
- TensorFlow Lite
- Transfer Learning
- Fine-Tuning
- Convolutional Neural Networks

### Data and Evaluation
- NumPy
- scikit-learn
- Matplotlib
- Confusion Matrix
- Precision
- Recall
- F1 Score

### Development
- Python
- Jupyter Notebook
- Git
- GitHub

## Collaboration and My Contribution

ZooTag was developed as a **collaborative AI/Machine Learning course project**.

I contributed across all major stages of the project, including:

- Data preparation
- Image preprocessing
- Data augmentation
- Model architecture and development
- Transfer learning
- Model training
- Fine-tuning
- Model evaluation
- Confusion matrix and classification analysis
- TensorFlow Lite conversion
- Float16 optimization
- Inference testing
- Interpretation and analysis of the results

Working across the full project pipeline gave me hands-on experience with both model development and the practical considerations involved in preparing a trained model for more efficient inference.

## What I Learned

Through ZooTag, I developed practical experience with:

- Building an end-to-end deep learning workflow
- Applying transfer learning to a relatively small dataset
- Fine-tuning pretrained neural networks
- Using data augmentation to improve generalization
- Evaluating models beyond simple accuracy
- Identifying class-specific strengths and weaknesses
- Understanding the effect of fine-tuning on model performance
- Converting TensorFlow models to TensorFlow Lite
- Applying float16 optimization
- Running lightweight model inference
- Collaborative machine learning development

## Relevance to Edge AI

The TensorFlow Lite stage introduced deployment-oriented considerations such as model size, inference efficiency, and lightweight execution.

This gave me practical exposure to concepts relevant to edge AI and on-device machine learning, particularly how trained models can be optimized for environments with more limited computational resources.
