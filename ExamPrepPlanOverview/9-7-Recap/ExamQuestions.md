# Practice Exam — 9/7 Recap

30 questions in AWS Certified Machine Learning Engineer – Associate style, covering Domain 1 (Data Preparation for Machine Learning) plus the ML fundamentals covered so far.

Answers and explanations are in `AnswerKey.md`. Recommended: 45 minutes, closed notes.

---

### 1.
A company stores 40 TB of raw clickstream logs in JSON, product images, and relational sales tables. The data science team needs a single centralized location that accepts all three without requiring a schema to be defined up front, and that can later feed both SageMaker AI training jobs and business intelligence tools.

Which storage approach meets these requirements?

- A. An Amazon Redshift data warehouse with the images stored as BLOB columns
- B. An Amazon S3 data lake with the raw data stored in its native formats
- C. An Amazon RDS for PostgreSQL database with a table for each source
- D. An Amazon EBS io2 volume attached to a large EC2 instance

---

### 2.
An ML engineer is training a deep learning model on a 3 TB dataset. Training shuffles records randomly at the start of every epoch, and the training job is currently bottlenecked on data read latency.

Which storage configuration BEST addresses the bottleneck?

- A. Stream the dataset directly from Amazon S3 using SageMaker AI pipe mode
- B. Store the dataset on an Amazon EBS gp3 volume
- C. Store the dataset on FSx for Lustre
- D. Store the dataset on Amazon S3 Glacier Instant Retrieval

---

### 3.
A team runs a distributed preprocessing job across 12 Amazon EC2 instances. Every instance must read and write the same 500 GB working dataset concurrently, and the team wants to avoid copying the dataset onto each instance.

Which AWS storage service should the team use?

- A. Amazon EBS
- B. Amazon EFS
- C. EC2 instance store
- D. Amazon S3 Standard-Infrequent Access

---

### 4.
An analytics team stores 5 years of transaction history in Amazon S3. Most queries select 3 columns out of 80 and aggregate over billions of rows. The team wants to minimize the amount of data scanned per query.

Which file format should the team use?

- A. CSV
- B. JSON Lines
- C. Apache Parquet
- D. Apache Avro

---

### 5.
A company must ingest streaming IoT telemetry and land it in Amazon S3 for a nightly batch training job. There is no requirement to process individual events as they arrive, and the team wants the LEAST operational overhead.

Which service should the company use?

- A. Amazon Kinesis Data Streams with a custom consumer application on EC2
- B. Amazon Data Firehose
- C. Amazon Managed Service for Apache Flink
- D. Amazon MSK with a Kafka Connect S3 sink

---

### 6.
A fraud detection system must score each incoming transaction against a SageMaker AI endpoint within 200 milliseconds of the event being produced. Multiple downstream applications also need to consume the same event stream.

Which solution meets these requirements?

- A. Amazon Data Firehose delivering to Amazon S3, with a scheduled Lambda function reading new objects
- B. Amazon Kinesis Data Streams with an AWS Lambda consumer that invokes the SageMaker AI endpoint
- C. AWS Glue ETL jobs scheduled every 5 minutes
- D. Amazon DynamoDB Streams with a batch export to Amazon S3

---

### 7.
A streaming pipeline must compute a 5-minute rolling average of sensor readings per device and write the result to SageMaker Feature Store before the data is used for inference.

Which service should be used to compute the rolling average?

- A. Amazon Data Firehose transformation with AWS Lambda
- B. Amazon Managed Service for Apache Flink
- C. Amazon Athena federated queries
- D. Amazon Kinesis Data Streams enhanced fan-out

---

### 8.
A company already runs Apache Kafka on-premises with dozens of existing producer and consumer applications. The company wants to move to a managed service on AWS without rewriting application code.

Which service should the company choose?

- A. Amazon Kinesis Data Streams
- B. Amazon MSK
- C. Amazon Data Firehose
- D. Amazon SQS

---

### 9.
An ML engineer must move 90 TB of historical training data from an on-premises data center to Amazon S3. The site has a 50 Mbps internet connection that is also used for production traffic.

Which approach is MOST appropriate?

- A. AWS DataSync over the existing internet connection
- B. S3 Transfer Acceleration with the AWS CLI
- C. AWS Snowball Edge
- D. AWS DMS with Amazon S3 as the target

---

### 10.
A team needs to continuously replicate rows from a production Amazon RDS for MySQL database into an Amazon S3 data lake so that the data is available for model retraining, with minimal impact on the source database.

Which AWS service is designed for this task?

- A. AWS Database Migration Service (DMS)
- B. AWS DataSync
- C. Amazon Data Firehose
- D. AWS Snowcone

---

### 11.
An ML engineer must join a 4 TB customer table with a 9 TB events table stored in Amazon S3, run automatic schema discovery, and avoid managing any cluster infrastructure.

Which solution meets these requirements with the LEAST operational overhead?

- A. Amazon EMR with a long-running Spark cluster
- B. AWS Glue crawlers with an AWS Glue Spark ETL job
- C. An AWS Lambda function using pandas
- D. Amazon Athena CTAS queries run manually each week

---

### 12.
A data engineering team has heavily tuned Spark code, custom Hadoop dependencies, and petabyte-scale jobs that require specific instance types and cluster-level configuration.

Which service is the BEST fit?

- A. AWS Glue
- B. Amazon EMR
- C. AWS Batch with Fargate
- D. Amazon Redshift Spectrum

---

### 13.
An ML engineer is enriching a primary customer dataset with optional loyalty program records. Every customer must remain in the output, even those with no loyalty record.

Which join type should the engineer use?

- A. Inner join
- B. Left outer join
- C. Full outer join
- D. Union (append)

---

### 14.
After merging two datasets, an ML engineer notices the output has 40% more rows than the primary input, and many columns contain unexpected null values.

Which two issues are the MOST likely causes? (Choose TWO.)

- A. Duplicate records in the secondary dataset causing row multiplication
- B. The use of a column-based file format instead of a row-based one
- C. Key format mismatches producing failed matches and null propagation
- D. Insufficient IOPS on the EBS volume holding the output
- E. The compute cluster being undersized for the job

---

### 15.
A RAG application must retrieve passages by semantic meaning, but also filter results by document owner and date range in the same query. The team wants a single managed service for both.

Which service should the team choose?

- A. Amazon S3 Vectors
- B. Amazon OpenSearch Service
- C. Amazon DynamoDB with a global secondary index
- D. Amazon Neptune

---

### 16.
A team already runs Amazon Aurora PostgreSQL and stores customer records there. They want to add semantic search over customer support notes without introducing a new database service, and they want embeddings stored alongside the relational data.

Which solution meets these requirements?

- A. Enable the pgvector extension on Aurora PostgreSQL
- B. Export the notes to Amazon OpenSearch Service and query with k-NN
- C. Store the embeddings in Amazon DynamoDB and scan for nearest neighbors
- D. Store the embeddings as Parquet files in Amazon S3 and query with Athena

---

### 17.
An ML engineer is choosing a similarity metric for a semantic search index. The embeddings vary widely in magnitude, and only the direction of the vector should influence relevance.

Which metric should the engineer use?

- A. Euclidean distance
- B. Dot product
- C. Cosine similarity
- D. Manhattan distance

---

### 18.
A company wants a fully managed RAG workflow that handles document chunking, embedding generation, and vector storage without the team writing an ingestion pipeline.

Which solution meets this requirement?

- A. Amazon Bedrock Knowledge Bases
- B. Amazon SageMaker AI Processing jobs with a custom chunking script
- C. Amazon OpenSearch Service with an ingest pipeline the team builds
- D. AWS Glue ETL jobs calling an embedding model

---

### 19.
A team is preparing a large policy manual for retrieval. Sections vary widely in length, and answers frequently span an entire subsection. Retrieval quality is poor because chunks cut sentences in half.

Which change is MOST likely to improve retrieval quality?

- A. Reduce the fixed chunk size to 100 characters
- B. Use semantic or hierarchical chunking that respects document structure
- C. Switch the distance metric from cosine similarity to Euclidean distance
- D. Increase the number of vector dimensions in the index

---

### 20.
A company trains a model with a Spark job that computes features in batch, but the real-time endpoint recomputes the same features with a separate Lambda function. Predictions in production are noticeably worse than in offline evaluation.

What is this problem called, and which service addresses it?

- A. Data drift; Amazon SageMaker Model Monitor
- B. Training-serving skew; Amazon SageMaker Feature Store
- C. Overfitting; SageMaker automatic model tuning
- D. Label leakage; SageMaker Clarify

---

### 21.
An ML engineer must retrieve the latest feature values for a single customer during real-time inference with low latency, and must also pull years of historical feature values for a training job.

Which two actions should the engineer take? (Choose TWO.)

- A. Call GetRecord against the SageMaker Feature Store online store during inference
- B. Call GetRecord against the SageMaker Feature Store offline store during inference
- C. Query the offline store with Amazon Athena for the training dataset
- D. Query the online store with Amazon Athena for the training dataset
- E. Use the PutRecord API to read historical features for training

---

### 22.
A Kinesis Data Streams application shows high write throughput on a small number of shards while other shards remain nearly idle, and producers are receiving throughput exceeded errors.

What is the MOST likely cause?

- A. The stream is configured with too many shards
- B. The partition key produces uneven data distribution across shards
- C. The consumer is using enhanced fan-out
- D. The records are compressed before being written

---

### 23.
An ingestion pipeline making one API call per record is hitting service throttling and high per-record network overhead.

Which two optimizations directly address this? (Choose TWO.)

- A. Batch multiple records into fewer API calls
- B. Compress records before transfer
- C. Convert the data from Parquet to CSV
- D. Increase the retention period on the stream
- E. Switch the storage class to S3 Glacier Flexible Retrieval

---

### 24.
An ML engineer must monitor throughput, IOPS, latency, and utilization for the storage and streaming services in an ingestion pipeline, and alarm when a resource approaches a hard limit.

Which service should the engineer use?

- A. AWS CloudTrail
- B. Amazon CloudWatch metrics
- C. AWS Config
- D. AWS X-Ray

---

### 25.
A dataset contains a `country` column with 60 distinct values that have no inherent ranking. The team plans to train a linear model.

Which encoding approach is MOST appropriate?

- A. Label encoding, because it produces a single compact numeric column
- B. One-hot encoding, because the values are nominal and have no order
- C. No encoding, because linear models handle strings natively
- D. Log transformation of the category index

---

### 26.
A dataset includes a `shirt_size` column with the values `small`, `medium`, and `large`.

How should this feature be classified and encoded?

- A. Nominal; one-hot encode it
- B. Ordinal; encode it so the numeric values preserve the ranking
- C. Binary; map it to 0 and 1
- D. Continuous; standardize it to mean 0 and standard deviation 1

---

### 27.
A model is being trained on features where `annual_income` ranges from 20,000 to 500,000 and `years_of_experience` ranges from 0 to 40. The training algorithm is gradient based, and the income feature is dominating the model.

Which technique addresses this?

- A. Binning both features into deciles
- B. Feature scaling with normalization or standardization
- C. One-hot encoding both features
- D. Removing the income feature from the dataset

---

### 28.
A `home_price` feature has a long right tail, with a small number of very high values skewing the distribution.

Which transformation is MOST appropriate to reduce skew and limit the influence of the extreme values while keeping the feature numeric?

- A. One-hot encoding
- B. Log transformation
- C. Label encoding
- D. Min-max normalization

---

### 29.
An ML engineer wants to convert a continuous `age` feature into age ranges because the exact value matters less than the general range, and the model needs to capture a nonlinear relationship.

Which technique should the engineer use?

- A. Binning
- B. Standardization
- C. Dimension reduction
- D. Tokenization

---

### 30.
A retailer has an unlabeled dataset of customer purchase histories and wants to discover natural groupings of customers without predefined categories, then flag customers whose behavior differs sharply from every group.

Which two techniques apply? (Choose TWO.)

- A. Cluster analysis
- B. Binary classification
- C. Anomaly detection
- D. Linear regression
- E. Reinforcement learning
