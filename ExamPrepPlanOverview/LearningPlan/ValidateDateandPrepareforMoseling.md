# Validate Data and Prepare for Modeling
Final steps to get the data ready for modeling. This stage is all about validating data integrity and configuring the data for the model itself. Data integrity is the accuracy, completness, reliability, consistency, and secruity of your data. One of the biggest goals of calidation is catching bias. Class imbalance or CI, it measures whether one group or facet is underrepresented in the data set compared to another. For Generative AI workloads, validation has a slighlty different flavro. You're checking the integrity of prompt and response pairs,
Data Integriy: Accuracy,Completeness,Consistency, Reliabilty, and security.
Pre-training bias metrics: Class imbalance(CL) differnce in proprtions of labels (DPL) which measure outcomes.

## Data Cleaning
### Incorrect and Duplicated Data
Incorrect data: Datasets often contain incorrect or anomalous data points that you address before model training. Common issues include language differences, types from data entry.
Duplicated data:Recods in a dataset that contain the same info. The process of automating duplicate removal is called deduplication.

### Data Outliers