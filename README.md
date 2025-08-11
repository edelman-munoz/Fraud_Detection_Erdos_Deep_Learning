# Fraud_Detection_Erdos_Deep_Learning
We apply unsupervised deep learning algorithms to fraud detection for the kaggle IEEE-CIS Fraud Detection dataset
## Background
What separates fraud detection from other deep learning applications is that it is close to impossible for human beings to tell if a transaction is fraudulent just by looking at transaction data. This is not true in image classification, for example, where it is possible for humans to tell if the image is of a cat or a dog. In the absence of such human-generated benchmarks, we need to rely solely on machines to learn hidden patterns in the data, which would be invisible to the human eye.

## Problem Statement
Primary goal is for the deep learning model to outperform other more traditional unsupervised methods (clustering algorithms etc.). Preexisting models that incorporate these data sets mostly rely on supervised learning methods, so we'll implement traditional clustering algorithms to establish a baseline performance. Our goal is to build a model that outperforms the baseline in both precision and recall. 

## Objectives

-Use Gaussian Mixture baseline model
-Create a deep learning model with autoencoders that outperforms baseline model in AUC-ROC as well as both precision and recall for some chosen threshold
## KPIs
-Precision: To reduce false positives

-Recall: Heavy bias towards high recall because notifying users of a suspicios transaction and allowing them to cancel the card if the transaction is fraudulent is more important than making sure that all identified cases are definitely fraud

-AUC-ROC: For measure of quality of model independent of chosen fraud threshold

-Runtime: Not necessarily a performance metric of the model, but something we really want to emphasize to determine the tradeoffs made when we make a better model
## Stakeholders
We see this project being used by commercial banking and financial institutions to detect fraudulent transactions and alert card holders of possible credit card theft. We aim to provide an improvement from existing models. 

## Project Setup

## Data
All data is from the IEEE-CIS Fraud Detection detaset which can be found at the follwing link: 
https://www.kaggle.com/competitions/ieee-fraud-detection

It is a dataset of credit card transactions with almost 600K entries and 368 features. it's very messy data. Most features are unknown/proprietary so we don't know what they represent. Many columns have >86% missing values. 

## Approach

Baseline Models: 
Most viable baseline models based on runtime and performance metrics were a standard isolation forest and a Gaussian Mixture Model (GMM) and a multivariate Gaussian model (MG). The GMM performed the best of the baseline models, and was the baseline we chose to compare our deep learning model to. 

Deep Learning Model: 
We developed an autoencoder designed to learn a compressed representation of input data by minimizing the reconstruction error between the original and reconstructed inputs. The model uses three linear layers with ReLU activations and dropout for regularization in the encoder. The model has 368 features that are pre-embedding; after embedding, they get mapped to low-dimensional dense vectors. 

![Autoencoder](/autoencoder_diagram.jpg)

## Results
-We adopted a refined train/validation/dev/test split strategy, separating normal and fraudulent transactions carefully to avoid data leakage.  

-Validation sets were used for early stopping and threshold determination; dev/test sets were strictly held out for final evaluation.  

-Thresholds were set by flagging the top 30% of UIDs or transactions with the highest reconstruction error as fraud.

### Deep Autoencoder Performance:

| Metric         | Average Rule       | Fraction Rule      |
|----------------|--------------------|--------------------|
| AUC-ROC        | 0.802              | 0.737              |
| Recall         | 71.82%             | 71.92%             |
| Precision      | 34.61%             | 34.12%             |
| Runtime        | ~20 minutes        | ~20 minutes        |

### Baseline Performance:

| Model          | AUC-ROC | Recall  | Precision | Runtime          |
|----------------|---------|---------|-----------|------------------|
| Multivariate Gaussian (MG) | 0.771   | 67.4%   | 18.4%     | ~10 seconds      |
| Gaussian Mixture Model (GMM) | 0.773   | 67.6%   | 18.4%     | ~40 seconds      |

![ROC_curves](/ROC_curves.png)
### Conclusions and Future Implications

The deep autoencoder model using UID-based detection with the Average Rule significantly outperforms baseline models in AUC-ROC, recall, and precision, highlighting its ability to identify more fraud cases while maintaining manageable false positives. The Fraction Rule slightly improves recall at the cost of some precision and AUC. Though the runtime is higher, the accuracy gains are promising for real-world fraud detection needs.

Our final model demonstrates that unsupervised deep learning with UID-level aggregation improves fraud detection metrics beyond traditional unsupervised methods. We plan to focus on further hyperparameter tuning, architectural exploration, and optimizing runtime for scalable deployment. 

## References
IEEE-CIS Fraud Detection Dataset: https://www.kaggle.com/competitions/ieee-fraud-detection/overview

## Team Members
This project is being developed for 2025 Summer Erdös Institute Deep Learning Boot Camp by:

-Adrian Wong 
-Yang Yang 
-Sara Edelman-Munoz
-Jude Pereira
-Mary Reith 
