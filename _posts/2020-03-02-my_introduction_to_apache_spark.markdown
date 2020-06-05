---
layout: post
title:      "My Introduction to Big Data on AWS"
date:       2020-03-02 19:28:03 -0500
permalink:  my_introduction_to_apache_spark
---


"Big data is like teenage sex: everyone talks about it, nobody really knows how to do it, everyone thinks everyone else is doing it, so everyone claims they are doing it..." - Dan Ariely, Duke Professor of Psychology and Behavioral Economics, Duke University

It is well understood amonst both data professionals as well as the general public that the amount of data in the world is growing at an expoential clip. Our society's growing reliance and dependence on technology has fed this monster which has proven to be a goldmine given the correct skillset to extract insights from it. 

I first began to realize the limitations of software with regards to handling large datasets while working as a junior data analyst at a private oil and gas operator in Houston, TX. A common joke amonst petroleum engineers in college is that we earn a degree in Microsoft Excel and learn a little about oil and gas when appropriate. Given my Excel expertise which had been honed over four undergraduate years I entered my first job assuming that the program could handle anything I threw at it. This hope was soon shattered as I began to attempt to analyze a few million rows of nationwide well completion data only to crash the program over and over again -  actively restraining myself from tossing my laptop into the market street eight stories below my office window. Keeping my cool, I began to explore alternative solutions and eventually ended up learning how to create and query a MySQL databases and utilzie Tableau for my data analysis needs. 

Similar to my previous experience I suspect that very soon in my career as a data scientist I will come across a time when my now beloved Pandas dataframe is nearing the limits of its capacity for big data analysis. As such, it is in my best interest to begin to explore some common big data tools and frameworks. I wish to complete future big data fed machine learning projects using AWS thus I will dedicate the remainder of this article to exploring some of the big data tools AWS has available. 

## Big Data on AWS

### EMR on AWS

Elastic Map Reduce (EMR) is a managed Hadoop framework which runs on EC2 instances. EMR Notebooks act as Jupyter Notebooks which run on your EMR cluster and may be integrated with other AWS services. This is very useful for machine learning. For example, if you have a very large dataset which must be transformed and / or normalized before being fed into a model, EMR allows you to distribute the workload amongst a cluster of computers which handle the data pre-processing in parallel. 

A cluster in EMR is a collection of EC2 instances, or nodes - specifically a master node, core node, and task nodes. The master node manages the cluster by distributing data and tasks to other nodes for processing. The core nodes act to execute tasks and host data on the Hadoop Distributed File System (HDFS). FInally, task nodes are used solely to execute tasks.  They are not hosting data on HDFS so you can add and remove them as needed. 

EMR Clusters may either be transient or long-running. A transient cluster will be automatically terminated once the work is completed. For example, this could include loading some data, tranforming the data, storing the data, and terminating the cluster. If you wish to actively interact with applications on an EMR cluster you may use a long-running cluster which may be manually terminated when you are finished. This type of cluster is better suited for exploratory data analysis. 

When you launch a cluster you select the frameworks and applications you need at that time. Once the cluster is spun up you can submit orders by connecting to the master node through the EC2 terminal or using ordered steps via the console.

### Apache Spark on AWS

The days Apache Spark has largely taken the place of MapReduce in the Hadoop hierarchy. Apache Spark is a large scale data processing engine built to quickly query, analyze, and transform huge amounts of data. Thanks to YARN, Apache Spark is able to work on top of your EMR cluster and utilize the underlying HDFS filing system. Compared to MapReduce, Apache Spark is able to execute batch-processing jobs 10-100x faster which has led to its huge popularity in recent years. 

Compenents of Spark include the Spark Core, and the libraries built on top of it - Spark Streaming, Spark SQL, MLLib, and GraphX. Spark Core is the foundation for the platform and at the lowest level utilizes a Resilent Distributed Dataframe (RDD) which is a collection of data partitioned across various compute nodes. Spark SQL is a distributed query engine which enables low latency, interactive queries. Notably, Spark SQL exposes a dataframe which takes the place of the RDD. This makes interacting with data via Spark code very similar to interacting with data on a Pandas dataframe or a SQL table. In fact, you can insert SQL commands to your Spark cluster. 

Spark Streaming ingests data in mini batches and is able to utilze the same application code as that used for batch jobs. Spark Streaming supports data ingestion from multiple sources including Twitter and Apache Kafta. Spark Streaming may also be integrated with Amazon Kinesis. 

Spark MLLib offers many common machine learning algorithms available - all implemented in a distributed and scalable fashion. This allows us to process massive datasets and train machine learning models across an entire cluster. Furthermore, Spark MLLib may be integrated with Amazon Sagemaker. However, Spark MLLib is likely going to become deprecated in the next major Spark release. 

More recently, Spark ML has been deployed as the higher-level  machine learning API being built on top of Spark DataFrames. It is rumoured that Spark ML was built using Scikit Learn as inspiration which makes it a very intuitive place to start machine learning with big data. 

Finally, a conversation about Spark would be incomplete without talking about Zepellin. Zepellin allows you to execute Spark code in an interactive notebook environment. Zepellin allows you to directly execute SQL queries and visualize data making data scientists feel at home just as we do with Jupyter Notebooks. 


