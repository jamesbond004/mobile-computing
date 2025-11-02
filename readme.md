Objective of Experiment

• We are predicting newborn birth weight using features: demographic, clinical data, medicine.

• Task is to create model to relate between features given and birth weight.

Data

• It contains 103400 rows and 37 features

• The target variable is BWEIGHT (birth weight).

• Features has few categorical and few numerical. Due to categorical, preprocessing steps is needed (encoding of categorical variables) and handling missing values is required.

Preprocessing Data

• Clean data: handle missing values

• one-hot encoding: Convert categorical to numerical data.

• normalize for models sensitive to scale.

• Split data 4-fold (75pc train, 25pc test) for model evaluation.

Model Evaluation

• Use metrics such as rmsle, MAE, MSE to compare models.

• Compare performance across models based on rmsle and cpu.

Observation

• There are complex interactions.

• The feature seems non-linear, linear regression can have basic model.

• Simple linear models underperform, failing to capture nonlinear and complex interactions.

• Data can be added to get better understanding, it is generic.

• Few features need medical classification, not consider every feature generic.
