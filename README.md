# :anatomical_heart::stethoscope: Cardiovascular diseases (heart failure)
> Kyana Marckx

This project focuses on preprocessing and feature analysis rather than comparing different models, as most related papers already do that extensively. Instead, a single model is trained (the one that generally performs best according to the literature) while experimenting with different preprocessing and feature analysis methods. This makes it possible to see how these choices affect model performance and to identify which preprocessing approaches lead to the best results.

## :heartpulse: Dataset
The dataset used in this project is the [Heart Failure Prediction Dataset](https://www.kaggle.com/datasets/fedesoriano/heart-failure-prediction), publicly available on [Kaggle](https://www.kaggle.com/datasets/).

## :heartpulse: Installations
Inside the `imports`-folder is a notebook `installations.ipynb` that contains all the installation commands for the used packages in this project. Run this file based on what packages are already installed on your device.

## :heartpulse: 1 - Exploration
Notebook `01-exploration.ipynb` dives into the exploration of the dataset; it executes the EDA (Exploratory Data Analysis) in multiple different ways. Some generated plots are also saved accordingly inside the `media`-folder. Notes and conclusions about the notebook can be found in `01-notes.md`.

## :heartpulse: 2 - Preprocessing
Notebook `02-preprocessing.ipynb` focuses on cleaning and preparing the data for modeling. It covers data cleaning, imputation, encoding of categorical features and the construction of reusable pipelines. Feature subsets are also defined in this step. Notes and conclusions about the notebook can be found in `02-notes.md`.

## :heartpulse: 3 - Modeling
Notebook `03-modeling.ipynb` handles the training of machine learning models using the preprocessing pipelines created earlier. Different feature subsets and preprocessing strategies are evaluated using k-fold cross-validation and hyperparameter tuning. Models are saved for later use and evaluation. Notes and conclusions about the notebook can be found in `03-notes.md`.

## :heartpulse: 4 - Evaluation
Notebook `04-evaluation.ipynb` evaluates the trained models on a held-out test set. Model performance is assessed using multiple metrics and visualizations such as ROC curves, with a focus on comparing preprocessing and feature selection choices. Notes and conclusions about the notebook can be found in `04-notes.md`.
