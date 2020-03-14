---
layout: post
title:      "Data Engineering on AWS for Data Scientists"
date:       2020-03-14 22:34:54 +0000
permalink:  data_engineering_on_aws_for_data_scientists
---


Machine learning in the cloud is rapidly becoming more popular for data scientists and corporations. By utilizing a Platform-as-a-Service (PaaS), such as Amazon Sagemaker, approach to machine learning there is no need to worry about the data storage and networking reguirements necessary to execute complex machine learning jobs. A PaaS approach to machine learning provides pre-configured environments on which a data scientist may train and host predictive models. For large scale jobs, PaaS ML eases the headache of running distributed machine learning jobs. 

It is my intention to utilize Amazon Sagemaker on the remainder of my projects in Flatiron School's Immersive Data Science program. I am primarily interested in Amazon Sagemaker compared to other machine learning platforms due to AWS's unquestionable dominance in cloud-based solutions. 

In order to take complete advantage of everything AWS has to offer data scientists it is helpful to understand the basics of the data engineering toolkit AWS provides. The purpose of this article is to provide a very high level summary of some of these tools. 

## Amazon S3

Amazon S3 (Simple Storage Service) is a service offered by Amazon which offers object storage via "buckets" with an intuitive web interface. Amazone S3  allows you to create a cost-effective, secure, and scalable data lake where data is protected by 99.999999999% durability. A data lake is simply a data repository which stores any type of data (structured, unstructured, or semi-structured) in its raw format. Eleven "9" durability implies that with ten million objects you could expect to lose one file about every ten thousand years (source AWS). Amazon S3 is the "backbone" of many of Amazon's machine learning services.

Amazon S3 has several tiers (and price points) of storage options from S3 Standard to S3 Glacier depending on how frequently you may need to access the data. Typically the more secure and accessible the data needs to be the more you're going to pay to store it. Furthermore, S3 allows you to create lifecycle rules which dictate the storage of data in the different tiers based time since creation. 

Regarding security, S3 offers multiple encryption options for objects ranging from being fully managed and handled by AWS to 100% client side encryption. Access to data may be defined via user-based and bucket-based policies. 

## Amazon Kinesis
Amazon Kinesis is AWS's answer to Apache Kafka and allows real-time "big data" analytics. Four services exist under the Kinesis umbrella - Kinesis Stream, Kinesis Analytics, Kinesis Firehose, and Kinesis Video Streams. The Kinesis architecture begins with incoming data (IoT, clickstreams, etc.) being unboarded into Kinesis Stream. Following this we may wish to perform real-time analytics on the data which is where Kinesis Analytics comes into play. Finally, Kinesis Firehose's purpose is to transfer data from Analytics to S3 buckets and / or Amazon Redshift (data warehouse) for deeper analytics or reporting. 

These are just two of many data engineering tools available on AWS. We will continue to return to machine learning using AWS in future blog posts. 


References:

[Data Lake Storage on AWS]https://aws.amazon.com/products/storage/data-lake-storage/)
