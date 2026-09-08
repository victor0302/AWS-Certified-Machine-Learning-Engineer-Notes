# Answer Key — 9/7 Recap Practice Exam

---

**1. B — Amazon S3 data lake.**
A data lake is a centralized store that holds structured, semi-structured, and unstructured data with no schema required up front, and it feeds both ML pipelines and analytics tools. A (Redshift) is a data warehouse optimized for structured relational data. C forces a rigid schema and does not fit images or raw logs. D is block storage tied to a single instance, not a centralized lake.

**2. C — FSx for Lustre.**
Randomized access across epochs needs low-latency random reads and high random IOPS. FSx for Lustre (and EBS io2) are built for that pattern. A is sequential streaming, which does not help random shuffling. B (gp3) does not deliver the random IOPS a heavy training workload needs. D is archival storage with the wrong latency profile entirely.

**3. B — Amazon EFS.**
EFS is a shared file system multiple EC2 instances can mount and access concurrently, which eliminates copying the dataset to every instance. An EBS volume attaches to one instance in the standard case, instance store is tied to a single instance lifecycle, and S3 Standard-IA is object storage with a retrieval-cost profile for infrequent access.

**4. C — Apache Parquet.**
Column-based formats store data by column, so a query touching 3 of 80 columns reads only those columns. CSV and JSON Lines are row-based and object-notation formats that force reading whole records. Avro is row-based and better suited to write-heavy or schema-evolving pipelines.

**5. B — Amazon Data Firehose.**
Firehose is purpose-built for delivering streaming data to storage destinations such as S3 and Redshift. It handles buffering, batching, and delivery with no consumer code. A, C, and D all require you to write and operate consumer or processing code you do not need here.

**6. B — Kinesis Data Streams with a Lambda consumer.**
Kinesis Data Streams gives sub-second latency plus fan-out to multiple consumers; the Lambda consumer calls the SageMaker AI endpoint. A introduces batch delivery latency. C is a batch ETL service. D is not a general-purpose event stream for this use case.

**7. B — Amazon Managed Service for Apache Flink.**
Flink performs windowed aggregations, joins, and feature computation on streams with exactly-once semantics, then writes results to Feature Store with PutRecord. A Lambda transform in Firehose is per-record and has no windowing state. C queries data at rest. D is a delivery mechanism, not a computation engine.

**8. B — Amazon MSK.**
MSK provides full Apache Kafka API compatibility, so existing Kafka producers and consumers run without code changes. Kinesis Data Streams and Firehose would require rewriting the applications, and SQS is a queue, not a Kafka-compatible stream.

**9. C — AWS Snowball Edge.**
Snow Family devices are for terabyte-to-petabyte transfers where network transfer is infeasible. 90 TB over a shared 50 Mbps link would take months. A and B are still bounded by the same constrained link, and D is for database replication, not bulk file transfer.

**10. A — AWS DMS.**
DMS is built for one-time or ongoing (CDC) replication from databases to targets including Amazon S3. DataSync moves files between file systems and AWS storage, Firehose ingests streaming data, and Snowcone is a physical transfer device.

**11. B — AWS Glue crawlers plus a Glue Spark ETL job.**
Glue is the serverless option: no clusters to configure, automatic schema discovery via crawlers, and pay per DPU-hour. A requires you to size and manage a cluster. C will not handle 13 TB in Lambda. D adds manual operational work.

**12. B — Amazon EMR.**
EMR is the cluster-based option that gives fine-grained control over node types and configuration, fits petabyte-scale jobs, and runs existing Spark or Hadoop code. Glue trades that control for a managed experience. C and D do not fit tuned Spark/Hadoop workloads.

**13. B — Left outer join.**
A left outer join keeps every record from the primary (left) dataset and fills nulls where the secondary dataset has no match, which is exactly the enrichment pattern. An inner join would drop customers with no loyalty record, a full outer join would also add unmatched loyalty records, and a union stacks rows vertically instead of joining.

**14. A and C — Duplicate records and key format mismatches.**
Duplicates on the join key multiply rows, and mismatched key formats cause failed matches that propagate nulls. These are the classic merge-time data quality problems, along with schema drift. B, D, and E are performance or format concerns, not causes of row inflation or nulls.

**15. B — Amazon OpenSearch Service.**
OpenSearch supports approximate k-NN vector search (HNSW and IVF via engines such as Faiss and Lucene) together with hybrid search and metadata filtering in one query. S3 Vectors targets low-cost vector storage, DynamoDB has no vector similarity search, and Neptune is a graph database.

**16. A — pgvector on Aurora PostgreSQL.**
pgvector adds vector similarity search to PostgreSQL on RDS and Aurora, so embeddings live alongside relational data and are queried with familiar SQL — no new service. B introduces a new service, C has no native similarity search, and D loses the tie to the relational records.

**17. C — Cosine similarity.**
Cosine similarity measures the angle between two vectors and ignores magnitude. Dot product weights similarity by magnitude, and Euclidean distance measures straight-line distance, so both are affected by vector length.

**18. A — Amazon Bedrock Knowledge Bases.**
Knowledge Bases provides a managed RAG experience that handles ingestion, chunking, embedding, and vector storage automatically. B, C, and D all require the team to build and operate the pipeline.

**19. B — Semantic or hierarchical chunking.**
Fixed-size chunking splits on character or token counts and ignores document structure, which cuts sentences and separates related content. Semantic and hierarchical strategies respect the document's natural boundaries. A makes fragmentation worse, and C and D do not address how the text was split.

**20. B — Training-serving skew; SageMaker Feature Store.**
When training features are computed by one code path and inference features by another, even small differences degrade predictions. Feature Store provides a single source of truth with an offline store for training and an online store for inference. The other options describe different problems.

**21. A and C — Online store GetRecord for inference, Athena on the offline store for training.**
The online store provides low-latency reads for real-time inference (GetRecord, or BatchGetRecord for multiple records). The offline store provides batch reads for training, queried with Athena SQL or by reading Parquet from S3. B and D invert the two stores, and E is a write API.

**22. B — The partition key produces uneven data distribution.**
Partition keys such as customer_ID or transaction_ID should spread records evenly across shards. A low-cardinality or skewed key sends most traffic to a few shards, producing hot shards and throughput exceeded errors while others idle. More shards do not cause this, and neither fan-out nor compression is the cause.

**23. A and B — Batching and compression.**
Batching combines multiple records into fewer API calls and network round trips, which directly addresses throttling and per-record overhead. Compression cuts bandwidth use and speeds data movement, at the cost of some processing overhead. C increases data size, and D and E do not affect write throughput.

**24. B — Amazon CloudWatch metrics.**
CloudWatch metrics is where you view and analyze throughput, IOPS, latency, and utilization for AWS services and set alarms. CloudTrail records API activity, Config tracks resource configuration, and X-Ray traces application requests.

**25. B — One-hot encoding.**
Country values are nominal, with no inherent order. Label encoding would imply a false ordering that a linear model would interpret as meaningful magnitude. C is incorrect because most ML algorithms require numeric input, and D is meaningless on an arbitrary category index.

**26. B — Ordinal, encoded to preserve the ranking.**
Small, medium, and large have a meaningful order, so an encoding that preserves that ranking retains real information. One-hot encoding would discard the ordering, the feature is not binary, and it is not a continuous measurement.

**27. B — Feature scaling.**
Normalization rescales values to a common range, often 0 to 1; standardization rescales to a mean of 0 and a standard deviation of 1. Either prevents features with larger magnitudes from disproportionately influencing the model and speeds up computation. A discards resolution unnecessarily, C does not apply to continuous features, and D throws away a predictive signal.

**28. B — Log transformation.**
A logarithmic function compresses a long right tail, normalizes skewed numeric data, reduces the effect of outliers, and pulls values closer to a normal distribution while keeping the feature numeric. Min-max normalization rescales the range but leaves the skew intact; the encoding options do not apply to a continuous feature.

**29. A — Binning.**
Binning groups numeric values into a smaller number of range-based categories. It reduces the effect of outliers and helps models capture nonlinear relationships, and it fits cases where the general range matters more than the exact value. Standardization keeps the feature continuous, dimension reduction removes features, and tokenization applies to text.

**30. A and C — Cluster analysis and anomaly detection.**
Both are unsupervised techniques, which suits an unlabeled dataset. Cluster analysis groups data by similar features, and anomaly detection identifies rare items that differ significantly from the rest. B and D are supervised and require labels, and E requires an environment with rewards and penalties.
