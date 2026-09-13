# Gender Detection using CNN

## Objective

The goal of this project is to develop a **Convolutional Neural Network (CNN)** model that can classify facial images into two categories: **Male** and **Female**.

The project covers image preprocessing, CNN model development, model training, evaluation, and prediction on new images.

## Dataset Overview

The dataset consists of two categories:

* `man/` — Contains images of male faces.
* `woman/` — Contains images of female faces.

### Dataset Details

* Total Images: **2,307**
* Training Images: **2,077**
* Validation Images: **230**
* Training/Validation Split: **90% / 10%**
* Image Size: **128 × 128 × 3**
* Batch Size: **32**

The dataset is divided into training and validation sets using Keras `ImageDataGenerator`.

## Data Preprocessing

The following preprocessing steps are applied:

* Images are resized to **128 × 128 pixels**.
* Pixel values are normalized to the range **0–1** using `rescale=1/255`.
* The dataset is divided into training and validation subsets using `validation_split=0.1`.
* Images are loaded in batches of 32.

## Model Architecture

A Convolutional Neural Network is developed to automatically learn facial features and patterns.

The architecture consists of:

1. **Conv2D — 32 filters** with ReLU activation
2. **MaxPooling2D**
3. **Conv2D — 64 filters** with ReLU activation
4. **MaxPooling2D**
5. **Conv2D — 128 filters** with ReLU activation
6. **MaxPooling2D**
7. **Flatten**
8. **Dense — 128 neurons** with ReLU activation
9. **Dropout — 50%**
10. **Dense — 1 neuron** with Sigmoid activation

The Sigmoid output layer is used for binary classification.

## Model Compilation & Training

The model is compiled using:

* **Loss Function:** Binary Crossentropy
* **Optimizer:** Adam
* **Learning Rate:** 0.001
* **Evaluation Metric:** Accuracy
* **Batch Size:** 32
* **Epochs:** 10

The model contains approximately **3.3 million trainable parameters**.

## Model Performance

The model achieved the following results:

| Metric                    |     Result |
| ------------------------- | ---------: |
| Training Accuracy         | **96.97%** |
| Best Validation Accuracy  | **90.00%** |
| Final Validation Accuracy | **89.57%** |

The best validation accuracy of **90.00%** was achieved during Epoch 4.

The difference between training and validation accuracy indicates some level of overfitting. This can be further addressed using techniques such as image augmentation, regularization, and transfer learning.

## Model Saving

The trained CNN model is saved and loaded using TensorFlow/Keras so that it can be reused for future predictions.

```text
gender_detection_model
```

## Prediction

A custom prediction function is implemented to classify new images.

The function:

1. Loads the input image.
2. Resizes it to **128 × 128 pixels**.
3. Normalizes the image pixels.
4. Passes the image through the trained CNN.
5. Returns the predicted class based on the model's probability.

Example predictions from the project:

* Male face image → **Male**
* New test image → **Female**

## Challenges

### Overfitting

During model training, the training accuracy became higher than the validation accuracy, indicating a degree of overfitting.

This means the model learned the training data very well but performed slightly worse on validation data.

## Possible Improvements

The model can be further improved using:

* Image augmentation such as rotation, zoom, and horizontal flipping
* Transfer learning using pretrained CNN architectures
* Batch Normalization
* Hyperparameter tuning
* Early Stopping
* Learning-rate scheduling
* A larger and more diverse dataset

## Project Workflow

```text
Face Image Dataset
        ↓
Image Preprocessing
        ↓
90/10 Train-Validation Split
        ↓
CNN Architecture
        ↓
Model Compilation
        ↓
Model Training
        ↓
Model Evaluation
        ↓
Model Saving
        ↓
New Image Prediction
```

## Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* Matplotlib
* Deep Learning
* Convolutional Neural Networks (CNN)

## How to Run

1. Clone or download this repository.
2. Open `Gender_Detection_1001_Project.ipynb` in Jupyter Notebook or Google Colab.
3. Download or provide the required face image dataset.
4. Update the dataset path in the notebook according to your system.
5. Run the notebook cells sequentially.
6. Train the CNN model.
7. Test the model using new images.

## Repository Structure

```text
Gender-Detection-CNN/
│
├── Gender_Detection_1001_Project.ipynb
└── README.md
```

## Conclusion

This project demonstrates the practical application of **Convolutional Neural Networks for binary image classification**.

The model achieved **96.97% training accuracy** and **89.57% final validation accuracy**, demonstrating good classification performance while also showing some scope for reducing overfitting.

The project provided practical experience in image preprocessing, CNN architecture design, model training, evaluation, model saving, and prediction on new images.
