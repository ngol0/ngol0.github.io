---
layout: page
title: Computer Vision Projects
description: self-directed learning projects
img: assets/img/4.jpg
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
        {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>

### 2. VAEs:
*  *Main Objective:* Train a Variational Autoencoder (VAE) using the anime faces dataset by MckInsey666. Then use this model to generate a gallery of anime faces.

*  *Resutls:*

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

### 3. GANs:
*  *Main Objective:* Build a Generative Adversarial Network (GAN) that generates pictures of hands. Trained on a dataset of hand images doing sign language.

*  *Resutls:* 62.50% of images were classified as hands with a confidence greater than 60% by a hand classifier.
  
### 4. Object Detection:
*  *Main Objective:* Retrain **RetinaNet** to spot Zombies using just 5 training images.
  
*  *Specific Tasks:* Setup the model to restore pretrained weights and fine tune the classification layers.
  
*  *Results:* The boxes my model generated match 99.58% of the ground truth boxes with a relative tolerance of 0.3.

### 5. Image Segmentation 1:
*  *Main Objective:* Build a model that predicts the segmentation masks (pixel-wise label map) of handwritten digits. This model will be trained on the M2NIST dataset, a multi digit MNIST.
  
*  *Specific Tasks:*  Build a Convolutional Neural Network (CNN) from scratch for the downsampling path and use a Fully Convolutional Network, FCN-8, to upsample and produce the pixel-wise label map. The model will be evaluated using the intersection over union (IOU) and Dice Score. 
  
*  *Results:* average IOU score of 75% when compared against the true segments.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

### 6. Image Segmentation 2: 
I did this project as an extension to the previous one with the purpose of learning more about U-net.

*  *Main Objective:* Load and augment the dataset. Create a U-Net model using [Segmentation Models](https://smp.readthedocs.io/en/latest/models.html#unet) with loaded Imagenet weights. Then train and evaluate the model for image segmentation task.
  
*  *Results:*

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

## Certificates
*  [Generative Deep Learning](https://www.coursera.org/account/accomplishments/verify/EOEXLWZN36BW)
*  [Advanced Computer Vision](https://www.coursera.org/account/accomplishments/verify/XRA8U3OZPRW8)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.


You can also put regular text between your rows of images, even citations {% cite einstein1950meaning %}.
Say you wanted to write a bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, _bled_ for your project, and then... you reveal its glory in the next row of images.



The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}

```html
<div class="row justify-content-sm-center">
  <div class="col-sm-8 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
  <div class="col-sm-4 mt-3 mt-md-0">
    {% include figure.liquid path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
  </div>
</div>
```

{% endraw %}
