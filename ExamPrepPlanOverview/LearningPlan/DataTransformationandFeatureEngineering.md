# Transform Data
## Introduction
The 3 techniques to walk through are data cleaning, catergorical encoding, and feature engineering. Raw data almost always has problems, missing values, duplicates, outliers. Noist inputs cost you accuracy and waste training compute. Once your data is clean, the next step is making it readable to an algorith,. Most ML algorithms only understand numbers, so categorical fields like country, color, or category need to be converted to numeric form. That process is called catergorical encoding. Take a color column, with label encoding you'd map them to 01, and 2. With one hot encoding, each color becomes its own column with a 1 or a 0. Feature engineering, is the step where youo use your knowledge of the problem to create new features or pick out the existing ones that matter the most. For genetative AI workloads, the transformation step looks a little bit different. You're not encoding categories. You're preparing documents for retrieval, splitting them into chunks, generating vector embeddings, and formatting prompt and repsonse pairs for fine tuning.
Transformation for generative AI:
Advanced text pre-processing, Foundation models read text as smaller units called tokens, so raw text is first broken down through tokenization. You can also standardize and augment text with domain-specific terms so the model handles speciliazed vocab well.
Embedding models converts text or images into numerical vectors that capture meaning. Item with similar meaning sit closer togehter in vector space, whihc supports semantic search and retrieval.
Document prepartion for RAG grounds a model's responses in your own content. Large documents are split into smaller chunks and tagged with metadata so a retrieval system can find the most relvanet passages.
Preparing data for fine-tuning adapts a foundation model to a specific task using curated examples.

## Categorical Encoding
Categorical encoding is the process of manipulating text-based variables into number-based variables.
Types of categorical values:
For example in a dataset that contains animal medical records, a cat's weight is considered numerical, and the breed of cat is considered catergorical.
Binary:
Nominal: categories with no inherent order, such as country or color
Ordinal: Categories with a meaning ful order.
When to encode:
Different ML algorithms might not require you to encode your variables. A random forest model can handle categorical features direcrtly, depending on the implementation.

## Feature engineering
After your data has been cleaned up and you've encoded it as necessary for your model, you can fine-tune or create new features in your dataset through feature engineering, a method for transforming raw data into more informative features that help models better capture the underlying relationships in the data.
Numeric feature engineering transfomrs numeric values. often by grouping different numeric values together. Text feature engineering transforms text, often splitting it into smaller pieces.

