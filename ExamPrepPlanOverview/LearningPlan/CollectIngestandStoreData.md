# Collect and Store Data
## Introduction
Explore one of the initial phases of the machine learning (ML) lifecycle: data processing. Focus on collecting, ingesting, and storing data for ML and AI workloads. How to recognize types of data and tell effective data from ineffective data. 
### Fundamental of Data Collectoin
Focused on collecting high-quality data that's both representative and valuable for training models. Think of this data as the backbone of your ML solution. What you actually want is data that's accurate, clean, and free of obvious erros. You also want it to be diverse. The first step is gathering all of that in one centralized place so we can clean it up and prepare it for training. At AWS, two patterns come up over and over for that central place, data lakes, and data warehouses.A data lake is a centralized store, sometimes described as a big dumping ground for all kinds of data that holds structured, semi-structured, and unstructured data. From there the data can flow into dbs, into ML pipelines, and into other tools for analysus. Data warehouses are different. They store structured data in relational tables optimized for online analytical processing, the kind of fast aggregation and reporting your business intelligence team needs.

Generative AI changes what you collect and what counts as quality. A traditional ML model learns from structured, labeled examples tied to a single prediction target. FM instead learn broad patterns from very large volumes of unstructured data such as text, images, and audio.

## Data Collection
Four data types categories: text, tabular, time series, and images.
Text data, is converted to numbers for use in machine learning models, especially for NLP tasks like sentiment analysis.
Tabular data refers to information that is organized into a table structure with rows and columns, such as the data in spreadsheets and databases. Ideal for linear regression models and other classic machine learning algorithms.
Time series data is collected over time with an inherent ordering that is associated with data points.

Structured data has a predefined schema: it is organized into rows and columns with consistent, well-defined fields, like the tables in a relational dbs or a spreadsheet.
Semi-structured data has organizational markets, such as tags, keys, or delimiters, but no rigid schema, so the fields can vary from record to record. Commmon examples include JSON documents, XML, and log files.
Unstructured data has no predefined schema or organization. It includes text docuements, images, audio, and video, and it makes up the majority of the data most organixation collect.

Data formats fall into three familes: row-based, column-based, and object notation.
Row-based data format organizes data where each row represents a single record or entity, and the columns represent each of the features of that entity. CSV Apache Avro and RecordIO
Column-based data format stores information with columns as the primary structure. In this format, queries extract insights from patterns within a column rather than the entire record. Apache Parquet and ORC.
Object-notation data format fits non-tabular, hierarchial data, such as graphs or textaual data. Object-notation data is structured into hierarchial objects with features and key-value pairs. JSON and JSONL

Data Visulization helps you gather insights into the quality and relevance of your data before training machine learning models. 
Exploratory data analysis uses visualization techniques(relationship analysis, distribution analysis, comparions, and compositions) to gain insight into a dataset.
Categorical data represents qualitative information using categories, such as gender, race, or dietary prefernces.
Numerical data represents quantitative mreasurements, such as age, income, or test scores.

## AWS Data Sources and Services
AWS Provides several storage services, such as Simple Storage Service(S3), Elastic Block Store(EBS), Elastic File System(EFS), and FSx.
Amazon S3 is a flexible, scalable, object storage service used for a wide range of application. Data lakes, websites, cloud-centered apps, backups, archives, analytics, and machine learning. Serves as a central data lake for ingesting, extracting, and transforming data to and from other AWS services used for processing tasks. Amazon S3 provides scalability, durability, and low cost, but is has higher latency compared to local storage. For latency-sensitive workloads, Amazon S3 might not be optimal. 
Amazon Elastic Block Store