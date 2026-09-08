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
Amazon Elastic Block Store provides persistent, block-level storage volumes for Amazon Elastic COmpute Clouse EC2 instances so you can scale storage performance. THe service integrates with SageMaker AI as a core componet for machine learning model training and deployment. Amazon EBS separates storage from EC2 instances, requiring more planning to allocate and scale volumes across instances. Instance stores simplify storage by tying storage directly to the Amazon EC2 instance lifecycle, which helps avoid separate volume management. EBS provides high-performance storage for ml applications requiring fast access to large datasets. io2 volumes provide the high random IOPS that training workloads need for frequent data access during gradient computation. EBS, can store pre-trained models artifacts for low-latency loading.
Elastic File System(EFS) is highly scalable, serverless, cloud-centered file storage service. You can set up file systems that automatically scale up to petabytes of data wihtout needing to provision or mange storage capacity. Provides a scalable, high-performance file storage system that can be accessed concurrently from multiple Amazon EC2 instances. Promotes high throughput and parallelism for data processing, media processing, and content management systems. EFS has higher pricing but offers streamlined scaling of shared file systems. EFS allows multiple EC@ instances to access the same datasets simultaneoulsy. Provides a scalable, shared file system that eliminates the need to copy large datasets to each compute instance.
FSx is a fully managed service that provides access to popular file systems like Lustre, NetApp, ONTAP, OpenZFS, and Windows File Server.
Throughput, latenct, scalability, elasticity, and data access patterns are driving factors of performance. Three characterisitics determine the storage service you need: I/O throughput and latency, scalbility and elasticity, and data access patterns.
Inference workloads need fast response times for delivering predictions but usually do not require high I/O performance. EBS gp3 volumes or EFS are well-suited for these needs. Training workloads, EBS volume provide the random IOPS that training workloads need. Real-time and streaming workloads, EFS file system allow low-latency, concurrent data access for real-tie and streaming workloads. Dataset storage, S3 is the choice for storing large datasets that do not need quick access.
Copy and load: the entire dataset is copied to the compute instance and loaded into memory before training begins. S3 as the source with EBS as the local working volume is a common pairing.
Sequential streaming: Data is read in order, streamed to the model as training progresses, without loading the full dataset into memory. This suits very large datasets. S3(Often through Amazon SageMaker AI pipe or fast file mode) and FSx for Lustre support sequential streaming efficiently.
Randomized access: The model accesses records in a random order, which is common when shuffling training data across epochs. This patterns needs low-latency random reads. EBS io2 volumes or FSx for Lustre as well-suited because they deliver the random IOPS this pattern demands.
A vector dbs stores high-dimensional vector embeddings and support efficient similarty search: k-nearest neighbors(k-NN) and approximate nearest neighbors(ANN).
RAG application moves data through five stages:
Chunk,Embed,Store,Retrieve,Augment.
Traditional databases excel at exact-match quieres but struggle with semantic queries. Vector dbs bridge this gap by storing numerical representations (embeddings) that capture semantic meaning. Cosine similarity, measures the angle between two vectors, ignoring magnitude. Dot product, measures similarity weighted by magnitude: considers both direction and length. Use when magnitude carries meaningul information. Euclidean distance, neasures straight line distance between two points. 
OpenSearch Service, supports appoximate K-NN search using the HNSW and IVF methods, implemented through engines such as Faiss and Lucene. Choose when you need hybrid search or metadata filtering alongside vector similarity.
RDS/ Aurora with pgvector, the pgvector extension adds vector similarity search to PostgreSQL on Relational Database Service (RDS) and Aurora. Store embeddings alongside relational data in the same db using familiar SQL. Choose pgvector when your team already uses PostgreSQL and wants vector capibility without a new service.
S3 Vectors, purpose-built vector storage within S2 that significantly lowers cost compared to dedicated vector databases.
Embedding dimensions, the distance metric, and the index type.
Chucking Strategies:Fixed-Size chucking, Semantic, and hierarchical.
Bedrock knowledge Base provides a managed RAG experience that handles ingestion, chunking, embedding, and vector storage automatically,

## Injest, Extract, and Merge Data
Data ingestion is the process of colecting data from diverse sources, such as dbs, data lakes, and straming sources.
When analyzing data, batch ingestion and real-time ingestion are the two main approaches.
Batch ingestion or historical analysis, collects and processes data on scheduled intervals, such as hourly, daily, and weekly.
Real-time ingestion streams data as it is generated, allowing for near real-time processing. Real-time ingestion for fraud detection, Batch ingestion for historical analysis for transactions.
AWS offers services that are purpose-bulit for ingesting and processing streaming data at scale. These services include Amazon Kinesis, Managed Streaming for Apache Kafka (Amazon MSK), and Amazon Managed Service for Apache Flink.
Amazon Kinesis is a streaming data service that can injest and process real-time data streams from different sources. Kinesis consists of several services that provide real-time data streaming and processing.
Kinesis Data Streams, you can build custom applications for processing real-time data at scale. Managed Service for Apache Flink is a fully managed service. You can run Java or Scala applications using open-source Apache Flink framework ro process srreaming data. Firehouse is a fully managed service that delivers real-time streaming data to destinations such as Amazon S3 and Amazon Redshift.
Kinesis Data Streams is primarily used for ingesting and processing data. Firehose provides a streamlined method of streaming data to data storage locations. Amazon Managed Service for Apache Flink provides consumption of streaming data in real time for analysis.
Data ingestion, use Kinesis Data Streams for streaming real-time data from streaming data sources to data consumers. You can use Firehose for streaming data to a data repository. Data processing, Managed Service for Apache Flink to perform real-time processing, transformations, and feature engineering on data. Real-time inference, Stream data processed by Amazon Managed Service for Apache Flink in real-time for machine learning processing to desintations, such as an SageMaker endpoint.
MSK is a fully managed service that makes it convenient for develpoers to build and run highly available, secure, and scalable applications. MSK uses Apache Kafka to enable real-time streaming data.
Scenario: You need to land streaming data in S3 or Redshift for later batch processing. 

Service: Amazon Data Firehose. 

Why: No consumer code needed. Firehose handles buffering, batching, and delivery automatically. It is purpose-built for delivery to storage destinations rather than per-event, low-latency consumption.
Scenario: You need to feed each event to an ML model within milliseconds. 

Service: Amazon Kinesis Data Streams with a Lambda or custom consumer. 

Why: Sub-second latency. You write the consumer logic that calls the SageMaker AI endpoint. Kinesis Data Streams provides the buffer and fan-out
Scenario: You need to compute aggregations, joins, or windowed features on streaming data before it reaches its destination. 

Service: Amazon Managed Service for Apache Flink. 

Why: Flink provides SQL and code-based stream processing with exactly-once semantics. Use it when the raw stream needs transformation before consumption.
Scenario: Your team already uses Kafka producers and consumers and wants managed infrastructure. 

Service: Amazon MSK. 

Why: Full Kafka API compatibility. No code changes required for existing Kafka applications.

Modern AI and ML workloads go far beyond structured tabular data. Foundation models on Bedrock increasingly accept multiple input.
AL and ML workloads consume data across four modalities(text, images,audio, and video)
Text is the most common, Text is small per file. PDF,TXT,HTML,JSON, and strucuted documents. Foundation of RAG corpora
Images are medium-sized per file, JPEG,PNG, and TIFF. Central to computer vision and multimodal AI, and supervised traaining requires labels.
Audio is defined by its sample rate and bit depth, with formats such as WAV,FLAC, and MP#. It is often transcribed to text before a model consumes it.
Video is the most storage-intenisce modality.
A typcail audio ingestion pipeline for speech AI: Collect, Standadize, store, transcribe, and catalog
Metadata enables discovery, filtering, lineage tracking, and compliance.

Data transfer and extraction tools:
AWS CLI, SDKS. S3 Transfer Acceleration uses CloudFront edge locations to accelerate large data transfers to and from Amazon S3. Database Migration Service (DMS) faciltates database migratoin between databases or to Amazon S3 by extracting data in various formats, such as SQL,JSON,CSV, and XML. Lambda is a serverless compute service that runs code without provisioning servers. AWS Glue is a fully managed extract, transform, and load (ETL) service that prepares and loads data. It can discover, catalog, and extract data from AWS Services.
DataSync, you can efficient;y transfer data between on-premises systems or AWS services by extracting data from sources. Snow Family devies(AWS Snowball Edge) are physical devices used to transfer large amounts of data into and out of AWS when network transfers are infeasible. Snow devices efficietnly and cost-effectibely move terabytes or petabytes of data into Amazon S3 for inital data transfer.
AWS has an array of storage and database options that provide flexible data extraction capabilites. S3 serving as a highly scable object storage service. EBS volumes provide storage for machine learing data. EFS allows creating shared files systems, extract data using CLI,SDKs, or with services like Transfer Family and DataSync that facilitate data transfers. RDS is a common source of extracting relational data baecause it offers managed databse instances. DynamoDB is a fully managed NoSQL database service provided by AWS. Opensearch Service provides managed search and analytics capabilites.
Choosing the right extraction approach:
Small, frequesnt extractions, use AWS Lambda triggerd by EventBridge schedules or S3 events.
Large-scale ETL, extracting and transforming large datasets from multiple sources, use AWS GLue. Glue crawlers discover your data, the Data Catalog orginaizes it, and Spark-based ETL jobs extract and transform at scale. 
Database migration, for one time or ongoing replication fro dbs to your machine learing data lake, use AWS DMS.
On premises or large physcial transfers. moving terabytes from onprem use DataSync for network based or Snow family
Data Merging
After sufficient data has been collected, merging or combining datasets is the next logical step for bringing data sources together.
Merge strategies:
Inner join: keeps only records that have matching kets in both datasets.
Left outer join: Keeps all records from the primary(left) dataset and adds matching records from the seconday dataset. Records without a match get null value for the secondary columns. Use left joins when enriching your main dataset with optional data.
Full outer join: Keeps all records from both datasets, filling in null values where matches are missing.
Union(append): Stacks datasets vertically rather than joining them horizontally. Both dataset must have compatible schemas.
AWS services for data merging:
AWS Glue is the serverless option: it manages the infra for you, so your team focuses on the merge logic instead of the cluster.
Best for: Serverless ETL with automatic schema discovery. 

Infrastructure: Fully managed, no clusters to configure. 

Scaling: Automatic, pay per DPU-hour consumed. 

When to choose: You want serverless, pay-per-use ETL without managing infrastructure. Your data fits in standard Glue job sizes. You need automatic schema inference using crawlers.
Amazon EMR is the cluster-based option: you size and tune the environment yourself, which fits petabyte-scale jobs and existing Spark or Hadoop code.

Best for: Large-scale distributed processing with fine-grained control. 

Infrastructure: Managed clusters with configurable node types. 

Scaling: Manual or auto-scaling cluster configurations. 

When to choose: You need fine-grained control over cluster configuration. Your data exceeds what Glue handles efficiently (petabyte scale). You have existing Spark or Hadoop code.
AWS Glue ETL workflow in three stages. Input: identify data sources. AWS Glue: create an AWS Glue crawler, then generate ETL scripts and define jobs. output: output the results.
EMR is a service for processing and analyzing large datasets using open-source tools of big data analysis.
EMR workflow in three stages. Input: ingest streaming data. EMR cluster distribute the data across the cluster, then tranform it. Output to Amazon S3.
ETL is done using Apache Spark Streaming API. Distrubute across EMR cluster
Data quality during merging. Key mismatches, normalzie key formats before merging. Duplicate records, verify output row counts and depulicate when needed. Schema drift. Null propagation.
Programming techniques for merging:
Python ETL with Pandas and Lambda, write ETL functions or script using Python libraries like Pandas to read diffrent sources, transform the data as needed, then merge and join the datsets together.
SQL-based merging with Athena and Redshift, use SQL to perform joins, unions, and other transformations direcetly within datasets stored in databsets stored in databases like Redshift.
Stream merging with Apache Flink: Managed Service for Apche flink to perform merging of real-time streaming data as the data is ingested.