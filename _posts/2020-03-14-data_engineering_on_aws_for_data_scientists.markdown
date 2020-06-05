---
layout: post
title:      "Data Engineering on AWS for Data Scientists"
date:       2020-03-14 18:34:55 -0400
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
Amazon Kinesis is AWS's answer to Apache Kafka and allows real-time "big data" analytics. Four services exist under the Kinesis umbrella - Kinesis Stream, Kinesis Analytics, Kinesis Firehose, and Kinesis Video Streams. The Kinesis architecture begins with incoming data (IoT, clickstreams, etc.) being unboarded into Kinesis Stream. Following this we may wish to perform real-time analytics on the data which is where Kinesis Analytics comes into play. 

Finally, Kinesis Firehose's provides an easy solution for batching, encrypting, compressing, and streaming data into data lakes (i.e. S3 buckets) and analytics tools (i.e. Amazon Redshift). Contrary to Kinesis Streams, Firehose will scale on demand (up to gigabytes per second) without any manual provisioning. 

## AWS Glue 

AWS Glue is an Extract Transform Load (ETL) application which contains crawlers capable of combing through massive amounts of structured and unstructured data (for example, in a S3 data lake) and cataloging that metadata into a central directory. The crawlers work through your data, either on a schedule or on demand, and determine data schemas and partitions. Once all of your metadata is in the central repository it may be used  when querying from other applications such as AWS Athena or Amazon Redshift. 

Glue ETL allows you to write ETL code using either Scala or Python and run jobs on a serverless Spark platform environment. This is very useful as it takes away the headache of having to worry about how to run your Spark cluster. 

## AWS Data Stores
We've already discussed S3, however, AWS contains multiple types of data stores which data scientists may find useful. 

Amazon Redshift is a large-scale (petabyte), scalable data warehousing technology which allows for rapid analytics on large datasets. This capability is due to its Massively Parallel Processing (MPP) and columnar data storage design. Redshift must first be provisioned and is best used as an OLAP (Online Analytical Processing) tool. Data may be loaded from S3 or queryed directly from S3 using Redshift Spectrum. 

Amazon RDS / Aurora are similar to Redshift, however, their design is row-based and they are designed for Online Transaction Processing (OLTP). Similary to Redshift, servers must be provisioned in advance. RDS may be used if you wish to store data regarding your model for exports, however, it will not be used directly for data analytics. 

DynamaDB is Amazon's NoSQL technology which supports key-value pair and document data structures. For data scientist and machine learning engineers on AWS, DynamoDB is a very useful place to store a machine learning model which must be served by an application. 

## AWS Data Pipeline

AWS Data Pipeline is an ETL service used to move data from one location to another. Data Pipeline is used to *manage* the ETL tasks - the actual ETL will be performed within an EC2 instance which is managed by Data Pipeline. For example, Data Pipeline could be used if you wish to perform some analytics in Sagemaker on data stored in DynamoDB or RDS, In this case we could execute Data Pipeline which would create an EC2 instance which would move the data to an S3 bucket. Data Pipeline is here to *orchestrate* the flow of data. 

Compared to Glue ETL, Data Pipeline gives you more control over the environment and resources used to run the code. 

## AWS Batch

AWS Batch allows you to run batch jobs based on Docker images. AWS Batch is fully serverless and takes care of provisioning the instances for you. Batch jobs may be scheduled using CloudWatch events or orchestrated using AWS Step Functions. Compared to Glue ETL, For example, an application for using AWS Batch would be to cleanup an S3 bucket and this task could be scheduled using CloudWatch. Compared to Glue, AWS Batch is a better choice for any non-ETL work. 

## AWS Step Function

AWS Step Functions allow you to design, assemble, and visualize data engineering and data science workflows. These workflows are easy to interpret, explain, and change if necessary. Step Functions track each step in your workflow and handle errors in a customized way. This greatly increases the resilency of your serverless application. 


These are the most common AWS data engineering tools used by data scientists and machine learning engineers. We will continue to return to machine learning using AWS in future blog posts. 

References:

[Data Lake Storage on AWS]https://aws.amazon.com/products/storage/data-lake-storage/)
