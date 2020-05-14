---
layout: post
title:      "Machine Learning in AWS Sagemaker: Part II"
date:       2020-04-19 20:01:37 -0400
permalink:  machine_learning_in_aws_sagemaker_part_ii
---


In today's post we are going to pick up where we left off exploring Sagemaker's machine learning libraries!

## Object2Vector
On our last blog post we reviewed Sagemaker's BlazingText which is useful for finding similarities between individual words. Object2Vector takes this a step further by allowing us to find similarities between documents. As an embedding layer, Object2Vector can take a high dimensional representation and condese it down to a lower dimensional representation. These vector may be used for tasks such as clustering similar documents, genre prediction, and of course recommendations. 

## Object Detection and  Image Classification
Our next Sagemaker function relates to computer vision, specifically Object Detection. This algorithm is not only capable of detecting object in an image but also will give you bounding boxes specifying where in the image those objects are located. Each classification also will yield a confidence score. This algorithm may be trained from scratch using your own data or may be used using weights from the ImageNet pre-trianed model. A hybrid approach would permit you to use the weights associated with the ImageNet model and then continue to train the algorithm using your own data. This would be very useful when you have a small dataset and would like to train just the final layers which pick up on higher dimensional features. 

The Image Classification algorithm is similar to the Object Detection algrothim but rather than identifying the location of an object will simply classify the object in the image. Similar to Object Detection this alrogithm may either be trained from scratch or used for transfer learning. 

## Semantic Segmentation
Semantic Segmentation will take the Object Detection alrogithm even one step further by offering pixel level objection location called a segmentation mask. This a very powerful algorithm which comes into play with fields such as medical imaging and self-driving cars which require a high level of grainularity. 

## Random Cut Forest
Random Cut Forest (RCF), an algroithm designed by Amazon engineers, is arguably their pride and joy. Random Cut Forest is Amazon's implementation of unsupervised anomaly detection. These anomalies could be breaks from consistent time series data (its primary use case) or unclassifiable data points. Each data point is given an anomaly score and statistically speaking anything more than three standard deviations away from the mean of the dataset is considered an anomaly. 

## Neural Topic Model
Neural Topic Model is an unsupervised method used to classify a document based and give it a "topic" on its contents. Topic is in quotations there as this is something that the computer assigns and is not something that is human readable. Each topic is a latent representation meaning that the topics are inferred from the word distributions in the corpus of documents. This method can of course be useful for classification of documents but may be used for summarization as well. For this method only the number of topics, not the topics themselves, is specified. 

