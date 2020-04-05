---
layout: post
title:      "Introduction to Machine Learning in AWS Sagemaker"
date:       2020-04-05 17:47:54 -0400
permalink:  introduction_to_machine_learning_in_aws_sagemaker
---

AWS Sagemaker is the heart of machine learning in AWS and is intended to handle the entire machine learning workflow from building, training, and deploying to production. Features ranges from offering Sagemaker notebooks for data preparation and feature engineering to spinning up EC2 instances to train models on large datasets. 

## Sagemaker Architecture

The root of the general architecture of Sagemaker is training data sitting in an S3 bucket. The job of Sagemaker is to provision hosts to train that data on. The model itself comes from a Docker image in an Elastic Container Registry (ECR). The training code will be taken from the Docker image and deployed to a fleet of hosts in Sagemaker to do the training. When the training completes Sagemaker will return that trained model to be stored in another S3 bucket. Once the model is ready to be deployed Sagemaker will reference another Docker image in the ECR which contains the inference code. The job of the inference Docker image is to take in incoming requests and use the saved model to make inferences based on that request. Sagemaker will spin up as many hosts as necessary to provide endpoints to the client application and serve incoming requests. 

![From AWS Website - General Sagemaker Architecture](https://docs.aws.amazon.com/sagemaker/latest/dg/images/sagemaker-architecture.png)

## Sagemaker Notebooks 



## Linear Learner

## XGBoost

## Seq2Seq

## DeepAR

## BlazingText

## Object2Vector
