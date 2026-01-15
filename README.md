# Capstone-Stroke-Risk-Prediction-A-Comparison-of-Clinical-and-Lifestyle-Factors
Yamini Sirobushanam 

1. Problem Statement:


Stroke is a major public health concern that can lead to long-term health issues if not identified or treated early. Preventative measures are equally important in reducing stroke risk. The objective of this project is to develop multiple predictive models that estimate the likelihood of a stroke occurring and to determine whether clinical risk factors or lifestyle related factors provide a strong predictive power. A successful model could identify high-risk individuals and prioritize preventative care or extensive monitoring. 

2. Model Outcomes: 


This project is formulated as a supervised binary classification problem, where the target variable indicates whether an individual has experienced a stroke (1=Yes, 0=No). Each model produces a probability score representing stroke risk. These probabilities are converted into high or low risk classifications using a decision threshold to better capture stroke cases. 

3. Data Acquisition:


The analysis uses a publicly available stroke prediction dataset, which contains demographic, clinical and lifestyle information. The variables included are: age, hypertension, heart disease, body mass (BMI), average glucose level, work type and smoking status. The dataset is highly imbalanced, with stroke cases representing approximately 5% of observations. Exploratory data analysis and visualizations were conducted to examine variable distributions, class imbalance, and evaluate the dataset's ability to predict stroke accurately. This influenced the type of modeling that would be done. 
 
4. Data Preparation:


Several preprocessing steps were performed to prepare the data for modeling. Missing BMI values were imputed using the median, and skewed continuous variables (BMI and average glucose level) were log transformed. Categorical variables one-hot encoded. The dataset was split into training(80%) and testing (20%) sets using stratified sampling to preserve the stroke rate in both sets. 

To support direct comparison between the type of risk factors, two seperate feature groups were constructed.

- Clinical Features: representing medical risk factors

- Lifestyle Features: representing behavioral and demographic factors 

Model Selection:
Multiple supervised learning algorithms were trained and evaluated to compare both algorithmic performance and predictive values of different feature groups 

First two baseline models were trained using specific feature sets:

- Random Forest Classifier:
This was selected for its ability to capture the nonlinear relationship between the target variables and the other factors, and its ability to be insensitive to extreme values and skewness.

- Weighted Logistic Regression Model:
This was selected because of its ability to address the class imbalance as well and provide another measure of predictive evaluation of the model.

Then, two additional models were trained using constrained feature sets.

- A Logistic Regression model was trained using clinical features only. 

- A Logistic Regression model was trained using lifestyle features only.

These feature specific models were treated as independent models rather than tuning steps. The purpose of doing so was to isolate and compare predictive strengths of clinical vs lifestyle factors under the same modeling techniques, and evaluate their predictive ability. 
To further improve performance with the Random Forest approach, grid search hyperparameter tuning with stratified five-fold cross validation was applied. Grid search was used solely to refine model parameters of the clinical feature set. 

5. Model Evaluation:


Because stroke cases are rare in the dataset, overall accuracy was not used as the primary evaluation metric. Instead, recall and Precision-Recall Area Under the Curve were utilized to better assess the model's ability to detect stroke cases. Class weighted was applied to reduce any misclassification of the minority class. Threshold tuning was also performed to improve recall while maintaining reasonable precision. The results indicate that the clinical feature model significantly outperformed the lifestyle feature model and the baseline models (both clinical and lifestyle), because it achieved a higher PR-AUC and recall score. In conclusion, medical risk factors, demonstrated by the Clinical Model are more informative predictors of stroke than lifestyle factors alone. 

6. Results and Conclusion:


Models that used clinical risk factors consistently performed better at identifying people at risk of a stroke compared to models that used only lifestyle factors. For instance, the clinical models correctly identified a much higher proportion of stroke cases compared to any of the lifestyle models. 

Baseline models that included all features also performed reasonably well, but seperating the features into clinical versus lifestyle revealed more information about what type of trained model was the most predictive. The lifestyle models detected fewer stroke cases, showing that behavioral and demographic factors alone are less informative. 

Tuning the settings of the clinical Random Forest model further proved its ability to identify high risk individuals, while tuning the lifestyle models would not have made a significant difference given their low performance. 

Overall, these results suggest that medical risk factors are the strongest predictors of stroke. More specifically, in this project, the Clinical Feature Set is the strongest predictor of stroke. 
