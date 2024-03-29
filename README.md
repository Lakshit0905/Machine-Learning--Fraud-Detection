## Machine Learning-Fraud Detection

This repo contains the Fraud Detection project as part of my data science portfolio. The objective is to detect fraudulent cases using a dataset of credit card transactions.

Problem Statement
Dataset
Exploratory Data Analysis
Traditional Method
Supervised Machine Learning
Unsupervised Machine Learning
Discussion and Conclusion

## Problem Statement

Organizations around the world lose an estimated five percent of their annual revenues to fraud, according to a survey of Certified Fraud Examiners (CFEs) who investigated cases between January 2010 and December 2011. Applied to the estimated 2011 Gross World Product, this figure translates to a potential total fraud loss of more than $3.5 trillion. (Source). In this project, we will explore how to fight fraud by using data. We will apply machine learning algorithms to detect fraudulent behavior similar to past ones. In fraud analytics we often deal with highly imbalanced datasets when classifying fraud versus non-fraud, and in this project we will examine some techniques on how to deal with that. For example, we will make use of imbalanced-learn, a Python module to balance data set using under- and over-sampling. More info here. To install this package with conda run the following:
conda install -c conda-forge imbalanced-learn

## Dataset

The dataset used in this project is downloaded from DataCamp's Fraud Detection in Python course. It is a dataset containing credit card transactions data. Fraud occurrences are fortunately an extreme minority in these transactions. However, Machine Learning algorithms usually work best when the different classes contained in the dataset are more or less equally present. If there are few cases of fraud, then there's little data to learn how to identify them. This is known as class imbalance, and it's one of the main challenges of fraud detection. Let's explore this dataset, and observe this class imbalance problem.

## Discussion and Conclusion

In this project, we have used both supervised and unsupervised machine learning techniques to detect fraud cases. We use supervised machine learning when we have fraud cases with labels. By combining the classifiers, we can take the best of multiple models. Random Forest as a standalone model was good in Precision but quite bad in terms of false negatives. Logistic Regression was good in Recall but very bad in terms of false positives. Decision Tree was in the middle. By combining these models together we indeed managed to improve performance. We have increased the cases of fraud that we are catching from 75 to 78, and reduced false negatives by 3, and we only have 4 extra false positives in return. If we do care about catching as many fraud cases as we can, whilst keeping the false positives low, this is a pretty good trade-off.

Model	Precision	Recall	f1-score	Accuracy	AUC ROC	TP	FP	FN	TN
Random Forest	0.99	0.82	0.90	0.9922	0.9743	75	1	16	2098
Logistic Regression	0.65	0.88	0.74	0.9749	0.9721	80	44	11	2055
Decision Tree	0.79	0.84	0.81	0.9840	0.9128	76	20	15	2079
Voting Classifier	0.94	0.86	0.90	0.9918	0.9738	78	5	13	2094

When we do not have labels for fraud cases (often in real life circumstances), we can use unsupervised machine learning techniques to distinguish normal from abnormal (thus potentially fraudulent) behavior. This requires an understanding of what is "normal" and we need to have a good understanding of the data and its characteristics. It is important to point out that it is difficult to validate unsupervised machine learning model results with normal performance metrics (e.g. accuracy, prevision, recall) because we don't have the actual fraud labels, or the ground truth. But there are other ways to do so such as check with fraud analysts to help us validate and see whether the cases we flagged are indeed suspicious , investigate and describe cases that are flagged in more detail and use model on past known fraud cases to see whether the model can actually detect those historical fraud cases correctly.
