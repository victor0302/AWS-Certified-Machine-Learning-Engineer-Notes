# Introduction

## Curriculum Introduction
First Phase: Start with data processing
2: Covers Model Development,
3: Focus on deploying trained models
4: Focuses on monitoring models after they're deployed

Machine learning lifecycle
Business goal,ML problem framing, Data processing, Model Development, Deployment, Monitoring

Phase 1: Data Preparation for ML and AI
Explore the specifics of collecting and storing data, transforming and engineering features from raw data, and validating data quality. Covers traditional data pipelines with services such as AWS Glue, EMR, and SageMaker Feature Store. Covers generative AI-specific preparation such as embedding models, retrieval augmented generation(RAG) document chunking, and fine-tuning data formats.

Phase 2: ML Model and FM Development
Covers model development, including choosing model approaches, training and fine-tuning models, and evaluating performance. SageMaker AI built-in algorithms, hyperparameter optimization, and the generative AI customization spectrum prompt engineering through model distillation. You also explore evaluation framework for traditional ML metrics and for generative AI-specific assessment such as large language model as a judge and RAG retrieval accuracy.

Phase 3: Focuses on deploying trained models and AI solutions into production. SageMaker AI endpoints, Bedrock, and agent framework. Resource provisioning with containers, auto scaling, and graphics processing unit (GPU) allocation. CI/CD automation covers traditional ML pipeline and generative AI workflows, including prompt versioning, agent deployment, and FM lifecycle management.

Phase 4: Focuses on operating ML and AI solutions after deployment. You explore monitoring techniques for model drift, agent performance, and FM quality, along with cost optimization through selection, token economics, and prompt caching. IAM for ML, Bedrock Guardrails, data encryption, and VPC config.

## Course Overview
Deep on machine learning basics and the algorithms behind common ML solutions. Examine how machine learning and AI evolved into deep learning and generative AI.

# Machine learning on AWS
## ML Algorithms and Models
ML is a subset of AI. ML focuses on developing algorithms that machines use to perform complex tasks without explicit instructions. A machine learning algo takes a different path. It finds the patterns between past customers and sales that are hidden in the historical data. The training process uses a large data set of historical examples where the inputs and the desired outputs are known.Those patterns are used to create a machine learning model. Features are identified parts of your data set that are important for determining accurate outcomes. Weights represent how important an associated feature is for the accuracy of that outcome. A higher likelihood of accuracy means a higher weight. The first feature is whether or not the item is a hat, it is. Features need to be expressed mathematically, the model converts that yes into a 1, and no would be converted to a 0. This customer has purchased at least one hat in the past. Based on that history, the trained model calculates a weight of .8. The second feature in our model is whether the product is from Brand Z. So the model converts that to a 1. This customer has also purchased at least one Brand Z item in the past. In a real machine learning model, many features and weights would be calculated with more mathematical complexity. There are 3 main categories you'll work with supervised learning, unsupervised learning, and reinforcement learning. Supervised learning algorithms are popular and widely applicable, a supervisor or teacher demonstrates with correct answer by labeling the data for the algorithm. Supervised learning splits into two subcategories, classification problems and regression problems. In classification problems, the goal is to assign data to one or more classes. Binary classification limits the target variable to just two options yes or no, 0 or 1. Multi-class classification assigns each observation to one of 3 or more classes based on its attributes. Regression problems map to continuous value, like an integer, instead of defined classes. Regression-based algorithm trains on labeled stock price data and predicts that the stock price of a company will move. With unsupervised learning, there's no teacher to provide labeled examples. Instead these algorithms detect emerging properties of the provided data set and construct patterns from them. In essence, the algorithms uncover and create their own labels. One common technique is dimension reduction. In reinforcement learning, the algorithm interacts with its environment and learns to take actions that maximize rewards. Incorrect actions are penalized. 

Unsupervised learning algo:
Dimension reduction reduces the number of features while preserving the most significant information.
Density estimation: estimates the underlying probability distribution of a dataset.
Cluster analysis: Groups data into clusters based on similar features.
Anomaly detection: identifies rare items or events that differ significantly from the rest of the data.

## Next Generation ML
Deep learning is a subset of machine learning that represents a huge leap forward in the capabilities of AI/ML. Computer vision, speech recognition, natural language processing and recommendation engines.
Deep learning uses artificial neural networks (ANNs) with multiple layers. Input layer, hidden layer: Edges, Corners and contours, object parts, then output layer.
Generative AI is a type of deep learning that can create new content and ideas and powered by very large machine learning models that are pre trained on vast collections of unlabeled data. These are commonly called foundation models (FMs)
Foundation models: Are Large neural networks trained on massive datasets that can be adapted to a wide range of downstream tasks. Instead of training a model from scratch, you start with an FM and customize it through fine-tuning, prompt engineering, or RAG. Bedrock provides access to foundation models.
RAG: combines a foundation model with a knowledge retrieval system. Instead of relying solely on what the model learned during training, RAG retrieves relevant documents from your data and includes them in the model's context. Bedrock Knowledge Bases provides managed RAG infra.
