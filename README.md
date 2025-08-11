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
-Precision

-Recall: Heavy bias towards high recall because notifying users of a suspicios transaction and allowing them to cancel the card if the transaction is fraudulent is more important than making sure that all identified cases are definitely fraud

-AUC-ROC: For measure of quality of model independent of chosen fraud threshold

-Runtime: Not necessarily a performance metric of the model, but something we really want to emphasize to determine the tradeoffs made when we make a better model
## Stakeholders
We see this project being used by commercial banking and financial institutions to detect fraudulent transactions and alert card holders of possible credit card theft. We aim to provide an improvement from existing models. 

## Project Setup

## Data
All data is from the IEEE-CIS Fraud Detection detaset which can be found at the follwing link: 
https://www.kaggle.com/competitions/ieee-fraud-detection

It is a dataset of credit card transactions with almost 600K entries and almost 400 features. it's very messy data. Most features are unknown/proprietary so we don't know what they represent. Many columns have >86% missing values. 

## Approach
Baseline Models: Most viable baseline models based on runtime and performance metrics were a standard isolation forest and a Gaussian Mixture Model (GMM). We list their performance metrics below. 

-Isolation Forest: Runtime was ~12 seconds, AUC-ROC was .738.
With fraud threshold at 30%, precision was .075 and recall was .646. 

-GMM: Runtime was ~40 seconds, AUC-ROC was .773.
With fraud threshold at 30%, precision was .184 and recall was .676. 




Deep Learning Model: 

## Results
### Conclusions and Future Implications
## References
IEEE-CIS Fraud Detection Dataset: https://www.kaggle.com/competitions/ieee-fraud-detection/overview

## Team Members
This project is being developed for 2025 Summer Erdös Institute Deep Learning Boot Camp by:

-Adrian Wong 
-Yang Yang 
-Sara Edelman-Munoz
-Jude Pereira
-Mary Reith 
