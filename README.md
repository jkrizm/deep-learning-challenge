# deep-learning-challenge

Overview of the analysis: The goal of this analysis is to develop a model for predicting whether applicants who are selected for funding by the non-profit "Alphabet Soup" are likely to be successful in the venture for which they are requesting the money. 

Results: Using bulleted lists and images to support your answers, address the following questions:

Data Preprocessing

What variable(s) are the target(s) for your model?
  All models: IS_SUCCESSFUL
What variable(s) are the features for your model?
  Model 1: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, ASK_AMT
  Model 2: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, STATUS, INCOME_AMT, SPECIAL_CONSIDERATIONS, 1/ASK_AMT
  Model 3: APPLICATION_TYPE, AFFILIATION, CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT, 1/ASK_AMT
What variable(s) should be removed from the input data because they are neither targets nor features?
  EIN and NAME were removed because they are neither targets nor features, but it is possible that some of the other data that the company provided should also be removed. As a first attempt, model 3 removed STATUS and SPECIAL_CONSIDERATIONS. To better   
  understand and analyze the data, the company should be consulted to better understand what information each parameter contains and whether any should be eliminated. Additionally, some of the data are largely skewed. For example, ASK_AMT has a very severe 
  right-skew. An attempt to normalize this was done in models 2 and 3 by taking the inverse (1/x) of the ASK_AMT. Further examination and data cleaning may be warranted to determine whether outliers for any variables should be removed or corrected. 

Compiling, Training, and Evaluating the Model

How many neurons, layers, and activation functions did you select for your neural network model, and why?
  All models used 2 layers. The first layer had 14 neurons and the second had 9. These numbers were chosen to roughly total 2/3 of the number of input features (40) + output features (1). Two layers were chosen given that most data were dichotimized dummies. Better understanding of what information the variables contain is warranted to aid in developing these parameters further. 
Were you able to achieve the target model performance? 
No
What steps did you take in your attempts to increase model performance?
  Model 2: Used exponential activation instead of sigmoid in the output layer, take the inverse of the ask amount to account for right skew.
  Model 3: Remove STATUS and SPECIAL_CONSIDERATIONS, take the inverse of the ask amount to account for right skew

Summary: Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
Using the current methods, the data combined with this model are insufficient to predict funding success. These data may not be appropriate for the deep neural network analyses that were chosen. Given that the outcome is binomial, a logistic regression may be sufficient to determine funding success. Furthermore, it is possible that some of the variables that were provided by alphabet soup are not relevant to these analyses. 
