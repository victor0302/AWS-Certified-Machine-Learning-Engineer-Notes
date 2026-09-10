# Validate Data and Prepare for Modeling
Final steps to get the data ready for modeling. This stage is all about validating data integrity and configuring the data for the model itself. Data integrity is the accuracy, completness, reliability, consistency, and secruity of your data. One of the biggest goals of calidation is catching bias. Class imbalance or CI, it measures whether one group or facet is underrepresented in the data set compared to another. For Generative AI workloads, validation has a slighlty different flavro. You're checking the integrity of prompt and response pairs,
Data Integriy: Accuracy,Completeness,Consistency, Reliabilty, and security.
Pre-training bias metrics: Class imbalance(CL) differnce in proprtions of labels (DPL) which measure outcomes.

## Data Cleaning
### Incorrect and Duplicated Data
Incorrect data: Datasets often contain incorrect or anomalous data points that you address before model training. Common issues include language differences, types from data entry.
Duplicated data:Recods in a dataset that contain the same info. The process of automating duplicate removal is called deduplication.

### Data Outliers
Outliers are data points that differ significantly from the majority of the data.
Detecting outliers with central tendency:
One way to detect the impact of outliers is to measure the central tendency of your data, using the mean and the median.
Natural and artifical outliers:

### Missing Data
Identify missing values, Python libararies such as pandas help you check for missing values.
Determine why values are missing, Missing at random, missing completely at random. Missing not at random.
Drop missing values.
Impute values, fills a missing value with an estimate

## Data Quality
Glue Data Quality, Glue DataBew, Comprehend process help you streamline the data validation process.
Common checks include completeness, uniqueness, freshness, and conformance.
Glue Data Quality is a managed service that helps you measure and monitor the quality of data in your data lakes and pipelines. Uses Data Quality Definition Language (DQDL) rules to check dimesnions such as completeness, uniquensess, and freshness.
Glue DataBrew is a visual data preparation tool that helps you clean and normalize data without writing code.
Comprehend is a natrual language processing (NLP) service that extracts insights from unstructured text.


## Labeling and Annotation
Annotation is the act of adding labels or metadata to raw data. Image data: image classification, Object detection, Semantic segmentation.
Text Data: Text classification, named entity recognition.
Choosing a workforce: Public crowdsourced workforce, Private workforce, Vendor workforce

## Data Integrity:
Prompt-response pair validation, fine-tuning data is usually organized as prompt-and-reponse pairs. Validation confirms that every pair is well-forned and consistent. 
Factual accuracy validation, a well-formed pair can still be factually wrong.
Content safety screening, you screen training data for harmful, toxic, or sensitive content before it reaches the model.
Protecting againt data poisoning, data poisoning is the deliberate insertion of malicious examples into a training set to change model behavior.
Prompt injection in training data, Mislabeled or adversarial exaples, Source provenance.

## Bias Detection
Bias in a dataset is any systematic imbalance that causes a model to favor one group or outcome over another. Managing bias is a two-part job. First, you detect and measure bias in the data. Then, you apply techniques to mitigate it before and after training.
Sources of bias: Sampling bias, measurement bias, label bias, proxy features
Measuring bias: To measure bias, you run a pre-training bias analysis on your dataset. You set the label column and the facet column.
Mitigating bias: after you detect and measure bias, you apply mitigation techniques to reduce it. Dataset splitting: split data into training, validation, and test sets. Shuffling, you randomize the order of records before splitting and training.  augmentation,You expand underrepresented groups by transforming the examples you already have, rather than creating data from scratch. Removing proxy features: you identify features that act as proxies for a sensitive attribure and remove or replace them
Multimodal Bias and Class Imbalance
To optimize a multimodal data distribution, you apply bias and distribution metrics to every modality and then balance them together.
Bias metrics apply to every modality: In numeric data, the facet is a column value such as age group. In text data, the facet might be the language. In image data, the facet might be a visual attribut.
Resolving class imbalance: Class imbalance, often needs active correction.
Best practices for addressing class imbalance: Understand your original data, Work with clean data, proritize privacy, and choose the right technique.
Techniques to resolve class imbalance: