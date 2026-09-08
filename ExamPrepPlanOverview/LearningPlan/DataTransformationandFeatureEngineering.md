# Transform Data
## Introduction
The 3 techniques to walk through are data cleaning, categorical encoding, and feature engineering. Raw data almost always has problems, missing values, duplicates, outliers. Noisy inputs cost you accuracy and waste training compute. Once your data is clean, the next step is making it readable to an algorithm. Most ML algorithms only understand numbers, so categorical fields like country, color, or category need to be converted to numeric form. That process is called categorical encoding. Take a color column, with label encoding you'd map them to 0, 1, and 2. With one hot encoding, each color becomes its own column with a 1 or a 0. Feature engineering, is the step where you use your knowledge of the problem to create new features or pick out the existing ones that matter the most. For generative AI workloads, the transformation step looks a little bit different. You're not encoding categories. You're preparing documents for retrieval, splitting them into chunks, generating vector embeddings, and formatting prompt and response pairs for fine-tuning.
Transformation for generative AI:
Advanced text pre-processing, Foundation models read text as smaller units called tokens, so raw text is first broken down through tokenization. You can also standardize and augment text with domain-specific terms so the model handles specialized vocab well.
Embedding models converts text or images into numerical vectors that capture meaning. Items with similar meaning sit closer together in vector space, which supports semantic search and retrieval.
Document preparation for RAG grounds a model's responses in your own content. Large documents are split into smaller chunks and tagged with metadata so a retrieval system can find the most relevant passages.
Preparing data for fine-tuning adapts a foundation model to a specific task using curated examples.

## Categorical Encoding
Categorical encoding is the process of manipulating text-based variables into number-based variables.
Types of categorical values:
For example in a dataset that contains animal medical records, a cat's weight is considered numerical, and the breed of cat is considered categorical.
Binary:
Nominal: categories with no inherent order, such as country or color
Ordinal: Categories with a meaningful order.
When to encode:
Different ML algorithms might not require you to encode your variables. A random forest model can handle categorical features directly, depending on the implementation.

## Feature engineering
After your data has been cleaned up and you've encoded it as necessary for your model, you can fine-tune or create new features in your dataset through feature engineering, a method for transforming raw data into more informative features that help models better capture the underlying relationships in the data.
Numeric feature engineering transforms numeric values. often by grouping different numeric values together. Text feature engineering transforms text, often splitting it into smaller pieces.

## Numeric Feature engineering
Numeric feature engineering involves creating a new feature by transforming or combining numeric values Common numeric feature engineering methods include feature scaling, binning, and log transformation.
Feature scaling aims to transform numeric values so that all values are on the same scale. This method takes large numbers and scales them down, so the ML algorithm can achieve quicker computations and avoid skewed results.
Normalization rescales the values of numeric features to a common scale, often between 0 and 1. This rescaling makes the values more comparable and prevents features with greater magnitudes from incorrectly influencing the model. 
Standardization is similar to normalization, but instead of scaling values from 0 to 1, it rescales the features to have a mean of 0 and a standard deviation of 1.
Binning is a technique to group numerical features into a smaller number of bins, or categories. The data is divided into these bins based on value ranges, which transforms a numeric feature into a categorical one. Binning reduces the effect of outliers and helps models capture nonlinear relationships. It is effective when the exact difference in numbers is not important, but the general range is.
Log transformation applies a logarithmic function to numeric features in a dataset. Log transformation is used to normalize skewed numeric data, reduce the effect of outliers, and keep values closer to a normal distribution. It can improve model performance when numeric features have highly skewed distributions or outliers.

## 9/8 Text Feature Engineering
You can use methods such as bag-of-words and N-gram to engineer your text-based features.

Bag of words model does not keep track of the sequence of words, but counts the number of words in each observation. Uses tokenization to create a statisitcal representation of the text.
N Gram model builds on bag of words by producing a group of words  n size. If n equals 2, a sliding window creates, each group of two words as a token pair and creates a statisitcal representaion of these token pairs.
Temportal Data, Temporal or time series, data is data involving time, like a series of dates. Feature engineering is important for temporal data because it can capture key trends, cycles, or patterns over time.
From word counts to embeddings:
Bag of words and N-gram produce sparse, count-based representations. They capture which words appear, but not what those words mean. Generative AI workloads instead use embedding models, which convert text into dense numerical vectors that capture meaning.

Feature Selection Techniques:
Feature selection instead reduces dimesntions by removing features, so your model can focus on the most revevant information.
Feature splitting and combining
You can use feature splitting and combining to provide the most useful information to your model.
Feature splitting breaks a feature into multiple derived features, expanding the feature space.
Feature combining aggregates multiple features into a new combined feature, reducing the feature space.
Principal componet analysis(PCA) is a statistical technique you can use for dimensionality reduction, which reduces the number of features in a dataset. The goal is to retain most of the variation in the original features while reducing the overall number of features to increase computational efficiency. Transforms the features into a new set of uncorrelated features called principal components, ranked by their variance, with the first components capturing most of the variance in the data.

## AWS Tools for Data Transformation
### Data transformation with AWS
AWS Glue and Glue DataBrew
AWS Glue is a fully managed extract,transform, and load(ETL) serivce that prepares and loads data for analytics. Auto-generates Python code to handle distributed processing, scheduling, and integration with data sources.
Glue DataBrew is a visual data preparation tool for cleaning, shaping, and normalizing datasets through an interactive interface without coding. Common use cases for the transformation stage:
Automated ETL pipelines, Data integration, data cleansing and standardization, data quality monitoring, feature engineering, final pretraining preparation

SageMaker Data Wrangler, available in SageMaker Canvas, helps you explore, clean, and preprocess data without writing code.
Transforming Streaming Data, Lambda, Spark, or EMR, and Managed service for Apache Flink for streaming workloads.
Lambda: Common use cases include normazling inconsistent streaming data into a standard format, and filtering a stream to drop unneeded data and reduce downstream cost.
Spark: You can write transformations in Spark SQL. Common use cases include real-time analytics on streams from Apache Kafka or Amazon Kinesis.
Managed Service for Apache: Runs Apache Flink applications that process streaming data continousuly with low latecy. Common use cases include computing real-time features from event streams, such as rolling counts and aggregates, and writing those featres direcetly to a feature store.

### Create and Manage Features with SageMaker Feature Store
Feature groups, You organize features into feature groups, which are collections of related features with a shared schema, similar to a database table. Centrailzed repository, standardized features, automated preprocessing, Managed feature pipelines, reuse for performance

## Generative AI Data preparation
### Advanced Text Pre-Processing
Preparing text for a foundation model means getting it into clean, consistent tokens the model can process efficiently.
Tokenization is the process of breaking text into smaller units called tokens. A token is oftern a word, part of a word, or a punctuation mark. A model has a context window measured in tokens. Most foundation model pricing is per token.
Normalzing text, before tokenization, you often normalize text so the model sees consistent input. Common steps include removing boilderplate like navigation menus or reparted headers.
Domain-specific augmentation, When you adapt a model to specialized domain, your text data might not cover enough variety. Augmentation expands a text dataset by generating new, realistic examples.
### Embedding Models
An embedding model converts data into a dense numerical vector that captures meaning.
Text and image embeddings, embeddings are not limited to text, image embedding models convert images into vectors so you can find visually similar images. Bedrock provides embedding models such as Amazon Titan Text Embeddings for text and Titan Mulitmodal Embeddings for text and image inputs
Choosing dimensions, an embeddings length is its number of dimensions. Amazon Titan Text Embeddings V2 lets you choose an output of 256, 512, or 1024.
Storing and using embeddings
After you generate embeddings, you store them in a vector database so you can search them by similarity.

### Document Preparation for RAG
Retrieval augmented generation (RAG) grounds a foundation models response in your own content. Instead of relying only on what the model learned during training, a RAG system retrieves relrvant passages from your documents and adds them to the prompt. Two preparation steps drive retrieval quality: chunking and metadata extraction.

Chunking:
Documents are usually too large to embed and retrieve as a single unit, so you split them into smaller shunks.Each chunk is embedded and store separately, and retrieveal retunrs the chunks closest in meaning to the query. Fixed-size default approach uses approximately 300 token per chunk with a 20% overlap. Semantic, groups text by meaning, keeping related sentences tgether and breaking where the topic shifts. Hierarchial, creates layers of chunk, with large parent chunks and smaller child chunks dervided from them. No chunking, treats each doucment as a single chunk. This suits content that is already short and self-contained.
Metadata Extraction:
Alongside each chunk, you attach metadata such as the source document, title, author, date, or category.
Managed RAG preparation:
Bedrock Knowledge Base automates much of this work. Point at a data source, choose a chunking strategy, and select an embedding model.

### Preparing Data for Foundation Model Customization
Three common ways to customize a model. Fine-tuning, continued pre-training, and distillation.
Fine-tuning adapts a model to specific task using labeled examples. You prepare a dataset of prompt-and-response pairs. Split off a validatoin set so you can measure how well the customized model generalizes. Bedrock supports reinforcement fine-tuning, which optimizes a model against a reward signal.
Continued pre-training adapts a model to a domain using large amounts of unlabeled text, rather than labeled pairs.
Distillation transfers knowledge from a large, capable teacher model to a smaller, cheaper student model.

### Data Privacy
Sensitive data and compliance. PII,PHI, and Data residency
Three techniques protect sensitive value in different ways.
Masking, replaces sensitive values with altered but realisiic-looking values or partailly hides them.
Redaction, removed sensitive values entierly and replaces them with a placeholder.
anonymizatoin, transforms data so an invididual can no longer be identifed, even indirectly. 
Comprehend, detects and classifies PII in text. Comprehend Medical: Detects PHI in Clinical text. Macie, discovers and classifes sensitive data, such as PII. Glue DataBrew: Applies redaction and masking transformation to columns during data preparation.
Bedrock Guardrails, for generative AI applications, sensitive information filters block r mask PII.