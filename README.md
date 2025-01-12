# Machine Learning Course Project

## Overview of the Repository

This repository contains all the code used for the Machine Learning course project. The project involves data annotation, feature extraction, model building and training. Below is a structured explanation of the repository and the methodology used.

### Directory Structure

- notebooks/**: Jupyter notebooks containing the preprocessing steps and the models respectively.
  - `preprocessing.ipynb`: All the preprocessing tasks excluding TF-IDF tokenization.
  - `classification.ipynb`: Random Forest Classification model.
  - `regression.ipynb`: Random Forest Regression / XGBoost model.
## Project Tasks

### Task 1: Multi-class Classification of Influencer Categories

- Predict one of the 10 classes.
- Accuracy metric will be used for evaluation.

### Task 2: Regression for Content Popularity

- Predict like_count.
- MSE will be measured for the log10.
## Methodology

### Data Annotation

Each team member was assigned a unique set of annotations to complete. The annotations involved inspecting Instagram profiles and answering questions about them, such as assigning categories, rating the quality of accounts, and answering yes/no questions. The quality of the annotations directly impacted the performance of the models.

### Feature Extraction

The feature extraction process involved several steps:

1. **Text Cleaning**: Cleaning and preprocessing text data from posts and profiles.
2. **TF-IDF Vectorization**: Converting text data into numerical features using TF-IDF vectorization.
3. **Log Transformation**: Applying log transformation to numeric features like comments count, like count, follower count, and following count.
4. **Emoji and Hashtag Extraction**: Separating emojis and hashtags from text data.
5. **Timestamp Processing**: Converting timestamps into year, month, day, and hour.

### Model Building and Training
#### Classification:
For the classification task, our idea was to flatten the posts by attaching the processed profile data to each post and have that as a line in our .jsonl file. This way we could train the model on a post based dataset.

We applied the same process to the test document. We took all the posts from the flattened database and tried to predict what each _post_ would be categorized as. After which we used a voting system among said posts for each user to determine which category the user belonged to.

We have also attempted to remedy the imbalance present among the categories in the dataset.

| Category             | # of users |
| -------------------- | :--------: |
| art                  |    191     |
| entertainment        |    323     |
| fashion              |    299     |
| food                 |    511     |
| gaming               |     13     |
| health and lifestyle |    503     |
| mom and children     |    149     |
| sports               |    113     |
| tech                 |    346     |
| travel               |    294     |

#### Regression:
As we had previously preprocessed data, we needed very little modification to the dataset to begin work with the models. We ran both Random Forest Regression and XGBoost and selected the best model.

For this model, we tried to improve our score using the following:
1. Parameter search using optuna
2. Selected the best model given the results
3. Using the minimum log MSE

## Results

### Classification Task

- **Round 1**:
  - Accuracy: 0.338496
  - f1-weighted: 0.352342

- **Round 2**:
  - Accuracy: 0.140969
  - f1-weighted: 0.120305

- **Round 3**:
  - Validation Accuracy: 0.8899
  - F1 Score (Micro): 0.79

### Regression Task

- **Round 1**:
  - Error: 6084.291474 

- **Round 2**:
  - Error: 4197.071141 

## Team Contributions

- **Ata Yekta Öz - 31057**: 
  Data Processing, Exploratory Data Analysis, Classification Model, Documentation
- **Samuel Shemsu Sani - 22616** : 
  Data Processing, Exploratory Data Analysis, Regression Model
