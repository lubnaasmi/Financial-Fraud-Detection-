# Fraud Detection Using Machine Learning

This project uses machine learning techniques to detect fraudulent financial transactions using a publicly available dataset. The goal is to build a reliable classification model that can distinguish between fraudulent and legitimate transactions.

## Data Dictionary

This dataset contains a mix of categorical and numerical variables. The data-dictionary below describes what each column represents:

* Type: The type of transaction   
* Amount: The amount of money transferred   
* NameOrig: The origin account name  
* OldBalanceOrg: The origin accounts balance before the transaction 
* NewBalanceOrig: The origin accounts balance after the transaction   
* NameDest: The destination account name   
* OldbalanceDest: The destination accounts balance before the transaction 
* NewbalanceDest: The destination accounts balance after the transaction 
* IsFlaggedFraud: A “naive” model that simply flags a transaction as fraudulent if it is greater than 200,000 (note that this currency is not USD)   
* IsFraud: Was this simulated transaction actually fraudulent? In this case, we consider “fraud” to be a malicious transaction that aimed to transfer funds out of a victim’s bank account before the account owner could secure their information.   


## Exploratory Data Analysis 

- No missing values were found in the dataset.

- Fraud is extremely rare (1,297 cases out of 1 million).

- All fraudulent transactions occur only in TRANSFER and CASH_OUT types.

- Many fraudulent transactions have a new balance of zero or show full withdrawal.

## Data Preprocessing

- Removed non predictive columns: nameOrig, nameDest, isFlaggedFraud.

- One-hot encoded categorical type column.

- Created interaction features (e.g., amount × type_TRANSFER) to capture fraud patterns.

- Scaled features using StandardScaler.

- Handled class imbalance using SMOTE to oversample the minority class.

## Modeling

Several models were tested:

#### Logistic Regression

* Baseline model

 * Accuracy: High, but very low precision and recall for fraud class 

#### Random Forest

* Precision: 62%, Recall: 90%

* Strong at reducing false positives but missed some frauds

#### XGBoost (Selected Model)

* Precision: 52%

* Recall: 95%

* F1-score: 0.67

* Chosen due to high recall and overall better fraud detection performance


## Conclusion

This project demonstrates the importance of handling imbalanced data and choosing evaluation metrics wisely. XGBoost, with SMOTE and feature engineering, proved most effective for catching fraudulent transactions.