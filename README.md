# Optimizing an ML Pipeline in Azure

## Overview
This project is part of the Udacity Azure ML Nanodegree. The purpose is to build and optimize an Azure ML pipeline using the Python SDK and a provided Scikit-learn model. The model created is then compared to an Azure AutoML run.

## Summary
This dataset contains data about bank clients, and the purpose is to predict if a client will apply for a loan.

Both the AutoML model and the logistic regressor resulted in the very similar prediction accuracy of 0.91.

## Scikit-learn Pipeline
Data stored in csv file is read. The data is cleaned by removing irrelevant features. Data is further cleaned through one hot encoding. Data is split into training and test sets. A training script is prepared to call the logistic regression algorithm. The training script is called several times with different hyperparameters. The hyper drive is run. We register the best model and save the found parameters.

The hyper parameter "C" was sampled using a uniform distribution, as this increases the probability of choosing the optimal value. The hyperparameter "max iteration" was sampled using choice function to reduce the number of tested parameters, and thus increase the training speed.

The early stopping policy helps to save time and money, while the chosen policy helps to stop when no improvement is observed for two consecutive runs.

## AutoML
The best model was "VotingEnsemble", in which several models are trained and each model votes for a prediction. The ensemble model then chooses the most likely class.

## Pipeline comparison
In terms of performance, the two best models were tied. This is not too surprising due to the limited time the models were tested for. 

## Future work
<li>Try more and different combinations of parameters to test the logistic regressor with</li>
<li>Train the AutoML for a longer time</li>
<li>Test different metrics on the AutoML</li>
