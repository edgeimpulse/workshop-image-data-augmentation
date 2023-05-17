# Image Data Augmentation Workshop

Welcome to the data augmentation workshop for image classification! 

## Check initial accuracy

Head to the following Edge Impulse project: [https://studio.edgeimpulse.com/public/226428/latest](https://studio.edgeimpulse.com/public/226428/latest)

Go to the *Data acquisition* page. Note the division of classes and the types of images we are working with. There should be 50 grayscale images with 96x96 resolution each of the following classes:
 * background
 * capacitor
 * diode
 * led
 * resistor

![Original dataset in Edge Impulse](assets/original-dataset.png)

Feel free to look at the *Classifier* page to examine the convolutional neural network architecture. We are using a simple model with 2 convolution (and pooling) layers with a final dense layer to perform image classification. You can see that our classes are fairly easily separated in the *Data explorer*.

![Original training results in Edge Impules](assets/original-model-training.png)

While 92.5% may look decent, keep in mind that the accuracy was around 97% on the training set. As a result, we run into a few problems with such a small dataset:
 * Model overfitting (low validation and test accuracy)
 * Model is not robust; it will struggle to generalize to components in different locations, zoom, crop, lighting, etc.

Head to the *Model testing* page and verify that our model is indeed overfit.

![Original test results in Edge Impulse](assets/original-test-accuracy.png)

## Question: how do we fix overfitting?

Think about some ways we can address model overfitting.

We will focus on one possible solution in this workshop: data augmentation.

## Data augmentation

Data augmentation is the process of artificially increasing our dataset by creating modified copies of our original samples.

This works on a variety of data types!
 * Images: crop, translate, rotate, add noise, etc.
 * Audio: add background noise, translate, shift frequencies, drop frequencies, etc.
 * Time series: add noise, translate, drop frequencies, etc. (see [this paper](https://arxiv.org/abs/2002.12478) for more information)

The [dataset in this repository](electronic-components-png-original.zip) is the same found in the public Edge Impulse project you just saw. We are going to augment this dataset and re-train the same model to see how it affects accuracy.



## Going further

### Transformation blocks



### Synthetic data generation

While samples generated via data augmentation can be considered a form "synthetic data," true synthetic data is AI generated! Imagine using [text-to-speech](https://cloud.google.com/text-to-speech) to automatically create keyword samples or [DALL-E 2](https://openai.com/product/dall-e-2) to generate images to use in your training set. 

If you would like to dig into this concept deeper, our own @jimbruges has a fantastic demo using Google's text-to-speech package to generate words for a keyword spotting dataset. Check out [his video here](https://www.youtube.com/watch?v=AoTB7eRjRiw):

[![Jim's synthetic data generation demo](https://img.youtube.com/vi/AoTB7eRjRiw/0.jpg)](https://www.youtube.com/watch?v=AoTB7eRjRiw)
