# 9/7 Recap

Recap and practice questions covering everything studied through September 7, 2026.

## What was covered today

**Collect, Ingest, and Store Data (Domain 1)**
- Data lakes vs. data warehouses; what "high quality" data means for traditional ML vs. foundation models
- Data types (text, tabular, time series, image), structure (structured, semi-structured, unstructured), and formats (row-based: CSV/Avro/RecordIO; column-based: Parquet/ORC; object notation: JSON/JSONL)
- Storage services and when each fits: S3, EBS (gp3, io2), EFS, FSx for Lustre
- Data access patterns: copy-and-load, sequential streaming, randomized access
- Vector storage and RAG: OpenSearch Service (k-NN, HNSW/IVF), RDS/Aurora pgvector, S3 Vectors, Bedrock Knowledge Bases; similarity metrics and chunking strategies
- Streaming ingestion: Kinesis Data Streams, Amazon Data Firehose, Managed Service for Apache Flink, Amazon MSK
- Extraction and transfer: Lambda, AWS Glue, DMS, DataSync, Snow Family, S3 Transfer Acceleration
- Data merging: join types, AWS Glue vs. Amazon EMR, merge-time data quality issues
- SageMaker Feature Store: online vs. offline store, feature groups, ingestion methods, training-serving skew
- Troubleshooting: CloudWatch metrics/logs, capacity vs. scalability failures, batching, compression, partitioning

**Transform Data and Feature Engineering (Domain 1, continued)**
- Data cleaning, categorical encoding (label vs. one-hot; binary, nominal, ordinal)
- Feature engineering overview; numeric feature engineering: scaling (normalization, standardization), binning, log transformation
- Generative AI transformation: tokenization, embedding models, document prep for RAG, fine-tuning data

**Earlier (9/6) also included in the questions**
- ML fundamentals: supervised (classification, regression), unsupervised (dimension reduction, clustering, anomaly detection, density estimation), reinforcement learning
- Deep learning, foundation models, and RAG basics

## Files

- `ExamQuestions.md` — 30 AWS-style practice questions
- `AnswerKey.md` — answers with explanations and why the distractors are wrong
