---
layout: post
title:      "Introduction to Machine Learning in AWS Sagemaker"
date:       2020-04-05 17:47:54 -0400
permalink:  introduction_to_machine_learning_in_aws_sagemaker
---

AWS Sagemaker is the heart of machine learning in AWS and is intended to handle the entire machine learning workflow from building, training, and deploying to production. Features ranges from offering Sagemaker notebooks for data preparation and feature engineering to spinning up EC2 instances to train models on large datasets. 

## Sagemaker Architecture

The root of the general architecture of Sagemaker is training data sitting in an S3 bucket (ideally in Protobuf format if to be used for deep learning). The job of Sagemaker is to provision hosts to train that data on. The model itself comes from a Docker image in an Elastic Container Registry (ECR). The training code will be taken from the Docker image and deployed to a fleet of hosts in Sagemaker to do the training. When the training completes Sagemaker will return that trained model to be stored in another S3 bucket. Once the model is ready to be deployed Sagemaker will reference another Docker image in the ECR which contains the inference code. The job of the inference Docker image is to take in incoming requests and use the saved model to make inferences based on that request. Sagemaker will spin up as many hosts as necessary to provide endpoints to the client application and serve incoming requests. 

![From AWS Website - General Sagemaker Architecture](https://docs.aws.amazon.com/sagemaker/latest/dg/images/sagemaker-architecture.png)

## Sagemaker Notebooks 
The most common way to use Sagemaker is via a Sagemaker Notebook. Sagemaker Notebook allows you access data from S3, pre-process and analyze that data, and train models. Popular libraries such as scikit learn and TensorFlow may be accessed via a Sagemaker Notebook in addition to Sagemaker's innate machine learning models which are available out-of-the-box - we will discuss some of these below. 

A cool aspect of Sagemaker Notebooks is they allow you to spin up instances directly from the notebook. Furthermore, once training is complete it's possible to deploy the model to fleet of endpoints directly from the notebook and allowing you make predictions at scale. 

## Linear Learner
Linear Learner is exactly what it sounds like - Sagemaker's linear regression algorithm implementation. It can be used for regression tasks or classification when a threshold is specified. 

Linear Learner accepts data in either a RecordIO-wrapped Protobuf (float32) or raw CSV format. For the raw CSV format, Linear Learner will assume that the first column is the target variable. Linear Learner accepts training data in either File or Pipe mode. File mode will copy all training data over from S3 all at once while Pipe mode data is streamed directly to training instances rather than being downloaded first. Pipe mode is advantageous when you have larger training sets (especially > 16 TB) as it will enable your jobs to train more quickly and use less disk space. 

Linear Learner is farily sophisticated for being a "simple" machine learning model. By using stochastic gradient descent (SGD) it can train large datasets much more quickly. Linear Learner has multiple optimization algorithm options to choose from including Adam and AdaGrad. When training commences, multiple models are trained in parallel and the algorithm chooses the best model during the validation phase. Of course, L1 (Lasso) and L2 (Ridge) regularization options are available to avoid overfitting and/or conduct feature selection. 

## XGBoost

## Seq2Seq

## DeepAR

## BlazingText

## Object2Vector
