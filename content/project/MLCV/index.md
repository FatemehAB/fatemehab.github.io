---
title: "Deep Learning for Pneumonia Diagnosis: A Study on Chest X-ray Image Classification"
date: 2019-12-01
tags:
  - Computer Vision
featured: true
image:
  caption: "An example of different categories of our dataset"
  focal_point: ""
  preview_only: false
---

Exploring machine learning and deep learning techniques to develop an automated system for accurately detecting pneumonia from chest X-ray images.

<!--more-->


### **Introduction**

Pneumonia is a serious infection of the lungs that affects millions of people globally, with young children, the elderly, and those with weakened immune systems at the highest risk. Rapid and accurate detection of pneumonia, particularly from chest X-rays, can save lives by enabling timely medical intervention. However, diagnosing pneumonia using X-ray images is a challenging task, even for experienced radiologists, due to its overlapping appearance with other lung conditions.

The recent rise of machine learning (ML) and deep learning (DL) methods in medical imaging has opened new possibilities for automating disease detection and improving diagnostic accuracy. In this project, we aimed to explore a range of machine learning approaches, combining both traditional ML techniques and advanced DL models to detect pneumonia from chest X-ray images.

Our objective was to evaluate the performance of different feature extraction methods and classifiers, including deep convolutional neural networks (CNN), on the pneumonia classification task. By comparing the accuracy of these models, we aimed to determine which method could best identify pneumonia in X-rays with minimal error.


### **Dataset and Problem Description**

The dataset used in this study consists of chest X-ray images of pediatric patients aged 1 to 5 years, provided by the Guangzhou Women and Children’s Medical Center. The images were categorized into two classes: **Normal** and **Pneumonia**. Pneumonia cases were further divided into bacterial and viral, adding complexity to the classification task. In total, we had 5,863 images, almost evenly split between the two categories.

Each image was preprocessed to ensure uniformity in size and format. Low-quality or unreadable images were removed to improve the accuracy of model training. The images were converted to grayscale and resized to 224x224 pixels, ensuring they could be processed by the deep learning models efficiently.

This dataset allowed us to simulate a real-world scenario where a machine learning model could be used to assist radiologists in diagnosing pneumonia by analyzing chest X-ray images.


### **Methodology**

Our methodology was divided into two major stages: **Feature Extraction** and **Classification**.

#### **1. Feature Extraction**

We used two main techniques to extract features from the X-ray images:

- **VGGNet**: We used a pre-trained VGG16 model as a feature extractor. VGG16 is known for its ability to capture high-level image features through a series of convolutional layers. The pre-trained model was fine-tuned on the X-ray dataset, and we extracted the output of the final convolutional layer to use as input features for the classifiers.
  
- **SIFT (Scale-Invariant Feature Transform)**: SIFT is a traditional feature extraction method known for its robustness to changes in scale, rotation, and illumination. We applied SIFT to extract a set of distinct keypoints from the X-rays, which were clustered using the Bag of Visual Words technique to generate fixed-length feature vectors.

#### **2. Classification**

For the classification step, we applied a variety of machine learning models to classify the X-rays as either normal or pneumonia-infected. The models used include:

- **Logistic Regression (LR)**: A statistical model commonly used for binary classification tasks. LR provided a baseline for performance comparison against more complex models.
  
- **Neural Networks (NN)**: We implemented both shallow neural networks (with two hidden layers) and deep neural networks (DNN) with multiple layers. The shallow networks provided a simpler approach, while DNNs were capable of learning more intricate patterns in the data.
  
- **Convolutional Neural Networks (CNN)**: We designed a CNN model from scratch to directly process the X-ray images. The CNN architecture included several convolutional layers followed by max-pooling layers, and fully connected layers at the end. This allowed the model to learn spatial hierarchies in the image data.

The models were evaluated based on their ability to correctly classify X-ray images into the appropriate categories, with a focus on accuracy, precision, recall, and F1-score.


### **Results**

After training and evaluating each model, the results were as follows:

| Model                  | Test Accuracy |
|------------------------|---------------|
| CNN                    | 94.60%        |
| SIFT + Simple NN        | 95.79%        |
| SIFT + DNN              | 94.76%        |
| VGG + Simple NN         | 97.12%        |
| VGG + DNN               | **98.27%**    |

The **VGGNet** combined with a **DNN** classifier achieved the highest accuracy at **98.27%**, outperforming all other models. This demonstrates that using a deep convolutional neural network like VGGNet to extract high-level features, followed by a deep neural network for classification, can significantly enhance the model’s ability to detect pneumonia from X-ray images.

Other models, such as the CNN trained from scratch and the SIFT-based approaches, performed reasonably well but did not match the accuracy of the VGGNet + DNN combination.


### **Evaluation and Statistical Analysis**

To further validate the performance of the models, we performed a t-test to compare the results of each model and determine whether the observed differences in accuracy were statistically significant. The t-test confirmed that the VGG + DNN model outperformed the other methods with high confidence.

Additionally, we analyzed the confusion matrices for each model to understand their strengths and weaknesses. The VGG + DNN model had fewer false positives and false negatives compared to the other models, indicating that it made more reliable predictions overall.


### **Conclusion**

In this project, we explored various machine learning and deep learning techniques for detecting pneumonia from chest X-ray images. Our findings indicate that **deep learning models**, particularly the **VGGNet + DNN** combination, provide the highest accuracy and reliability for this task. These results suggest that deep learning techniques are well-suited for medical imaging applications, where subtle patterns need to be detected in complex data.

For future work, expanding the dataset to include more diverse cases and experimenting with more advanced architectures such as ResNet or EfficientNet could further improve the model's performance. Additionally, real-time deployment of such models in clinical settings could significantly enhance diagnostic efficiency, especially in regions with limited access to specialized radiologists.


### **Future Directions**
  
- **Larger and Diverse Dataset**: Expanding the dataset to include more age groups, different types of pneumonia, and various levels of disease severity would allow for more robust training and better generalization.
  
- **Real-World Deployment**: Integrating this model into a real-world clinical setting, where it could assist radiologists in making faster, more accurate diagnoses, would be an exciting next step.
  
- **Further Model Enhancements**: Exploring state-of-the-art architectures like EfficientNet, or employing techniques like attention mechanisms, could push the model’s performance even further.
