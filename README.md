# Prediction Assignment Writeup

## Overview

This project is part of the **Practical Machine Learning** course and focuses on predicting the manner in which participants performed barbell lifts using accelerometer data collected from the belt, arm, forearm, and dumbbell.

The goal was to develop a classification model capable of predicting five exercise execution patterns represented by the `classe` outcome variable.

## Data

The analysis uses the Practical Machine Learning training and testing datasets.

* Training data: **19,622 observations and 160 variables**
* Testing data: **20 observations and 160 variables**
* Outcome variable: `classe`
* Exercise classes: **A, B, C, D, and E**

## Data Preparation

The data were examined for missing values and variables that were not appropriate as model predictors.

Variables with more than 90% missing values were removed. The following metadata and timestamp variables were also excluded:

* `X`
* `user_name`
* `raw_timestamp_part_1`
* `raw_timestamp_part_2`
* `cvtd_timestamp`
* `new_window`
* `num_window`

After cleaning, the training dataset contained **53 variables**, including the outcome variable, leaving **52 sensor-based predictors**.

## Modeling Approach

A **75/25 stratified train-validation split** was used to evaluate model performance while maintaining the class proportions of `classe`.

A **Random Forest classification model** was fitted using the `randomForest` package in R. The model used:

* **500 trees**
* **7 randomly selected predictors at each split**

The model was evaluated on the held-out validation dataset using a confusion matrix.

## Results

The Random Forest model achieved:

* **Validation accuracy: 99.59%**
* **Validation error rate: approximately 0.41%**
* **Initial Random Forest OOB error rate: approximately 0.49%**

A final Random Forest model was subsequently trained using the complete cleaned training dataset.

The final model had an **OOB error rate of approximately 0.30%**.

The variable-importance analysis identified several influential predictors, including:

* `yaw_belt`
* `roll_belt`
* `magnet_dumbbell_z`
* `pitch_belt`
* `magnet_dumbbell_y`

The final model was used to generate predictions for all **20 observations** in the testing dataset.

## Files

* **`Prediction_Assignment_Writeup.Rmd`** — R Markdown source containing the complete analysis and code.
* **`Prediction_Assignment_Writeup.html`** — Compiled HTML version of the analysis.
* **`README.md`** — Project overview and summary.

## Software and Packages

The analysis was conducted in **R** using:

* `caret`
* `randomForest`

## Conclusion

This analysis developed a Random Forest classification model for predicting barbell-lifting execution patterns from accelerometer measurements. The model achieved **99.59% accuracy** on the held-out validation dataset, while the final model trained on the complete cleaned dataset had an **OOB error rate of approximately 0.30%**. The final model was also used to generate predictions for all 20 observations in the provided testing dataset.

## Author

**Stephen Mikah Makoshi**
