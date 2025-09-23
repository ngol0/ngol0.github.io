---
layout: page
title: Computer Vision projects
description: self learning projects
img: assets/img/doggo.png
importance: 1
category: academic
related_publications: true
---

These are the projects from my self-directed learning. Most of them are from the two DeepLearning.AI courses by Andrew Ng: [Advanced Computer Vision](https://www.coursera.org/learn/advanced-computer-vision-with-tensorflow/) and [Deep Generative Modelling](https://www.coursera.org/learn/generative-deep-learning-with-tensorflow/). Each course consists of 4 modules, with one project per module. The project details for relevant topics could be found below. The topics and models covered in each module include:

* **Object Detection:** model architecture of R-CNN, Fast R-CNN, Faster R-CNN, finetune RetinaNet.

* **Image Segmentation:** model architecture of U-Net, segmentation implemention with FCN
  
* **Visualization and Interpretability:** visualize model predictions and understand CNNs

* **Deep Generative Modelling:** style transfer, VAEs and GANs

## Project Details
These projects explore various computer vision techniques and generative deep learning models. Each project focuses on applying a specific model or technique to a practical dataset.

### 1. Style Transfer:
*  *Main Objective:* Implement neural style transfer using the Inception model as feature extractor.

*  *Resutls:* A new image of the original dog (left) with the style of the right image.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/original.png" title="doggo" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/doggo.png" title="result" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### 2. VAEs:
*  *Main Objective:* Train a Variational Autoencoder (VAE) using the anime faces dataset by MckInsey666. Then use this model to generate a gallery of anime faces.

*  *Resutls:*

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vae.png" title="vae results" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### 3. GANs:
*  *Main Objective:* Build a Generative Adversarial Network (GAN) that generates pictures of hands. Trained on a dataset of hand images doing sign language.

*  *Resutls:* 62.50% of images were classified as hands with a confidence greater than 60% by a hand classifier.
  
### 4. Object Detection:
*  *Main Objective:* Retrain **RetinaNet** to spot Zombies using just 5 training images.
  
*  *Specific Tasks:* Setup the model to restore pretrained weights and fine tune the classification layers.
  
*  *Results:* The boxes my model generated match 99.58% of the ground truth boxes with a relative tolerance of 0.3.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/exe2.jpg" title="object detection" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### 5. Image Segmentation 1:
*  *Main Objective:* Build a model that predicts the segmentation masks (pixel-wise label map) of handwritten digits. This model will be trained on the M2NIST dataset, a multi digit MNIST.
  
*  *Specific Tasks:*  Build a Convolutional Neural Network (CNN) from scratch for the downsampling path and use a Fully Convolutional Network, FCN-8, to upsample and produce the pixel-wise label map. The model will be evaluated using the intersection over union (IOU) and Dice Score. 
  
*  *Results:* average IOU score of 75% when compared against the true segments.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/exe3.png" title="imgseg1" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### 6. Image Segmentation 2: 
I did this project as an extension to the previous one with the purpose of learning more about U-net.

*  *Main Objective:* Load and augment the dataset. Create a U-Net model using [Segmentation Models](https://smp.readthedocs.io/en/latest/models.html#unet) with loaded Imagenet weights. Then train and evaluate the model for image segmentation task.
  
*  *Results:*

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/more.png" title="imgseg2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Certificates
*  [Generative Deep Learning](https://www.coursera.org/account/accomplishments/verify/EOEXLWZN36BW)
*  [Advanced Computer Vision](https://www.coursera.org/account/accomplishments/verify/XRA8U3OZPRW8)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cert.png" title="cert1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/cert2.png" title="cert2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
