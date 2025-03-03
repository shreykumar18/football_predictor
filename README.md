# football_predictor

Football Match Outcome Prediction Using Bayesian Networks

Project Overview

This project aims to develop a predictive model for upcoming football league matches using machine learning, specifically Bayesian Networks. The dataset used for this project contains a variety of in-depth team and player statistics, allowing us to analyze past performance trends and predict match outcomes. The model is designed to forecast not only match results (Win, Draw, or Loss) but also key game statistics such as expected goals (xG) and shots on target.

Project Goals

Data Exploration & Preprocessing

Analyze the dataset for missing values and handle them appropriately.

Encode categorical features into numerical values.

Perform feature engineering such as rolling averages and home/away performance factors.

Model Selection & Training

Implement a Bayesian Network model to predict match results.

Compare performance against Naïve Bayes to assess the best probabilistic approach.

Evaluation & Analysis

Measure model performance using accuracy, precision, recall, and F1-score.

Analyze confusion matrices to identify misclassifications.

Optimize the model by adjusting feature selection and probability distributions.

Dataset Information

The dataset consists of three primary tables:

1 Games Data (Match-level stats)

Column

Description

gameID

Unique match identifier

homeTeamID, awayTeamID

IDs for home and away teams

homeGoals, awayGoals

Final score for home and away teams

homeProbability, drawProbability, awayProbability

Pre-match betting probabilities

2️ Team Statistics Data (Team-level match stats)

Column

Description

teamID

Unique team identifier

location

Home (h) or Away (a)

xGoals

Expected goals metric

shots, shotsOnTarget

Number of total & on-target shots

fouls, corners, yellowCards, redCards

Discipline stats

result

Match outcome (Win = 1, Draw = 0, Loss = -1)

3️ Shots Data (Individual shot records)

Column

Description

gameID

Match ID where shot occurred

shooterID, assisterID

Player IDs for shooter and assist provider

minute

Time of shot in match

situation

Open play, set piece, counterattack, etc.

shotType

Left foot, right foot, header, etc.

xGoal

Probability of scoring from the shot

⚙ Implementation Steps

1. Data Preprocessing

✔ Handled missing values: Filled missing numerical values with the median and categorical values with 'Unknown'.
✔ Encoded categorical features: Converted match results to numeric values (W = 1, D = 0, L = -1).
✔ Feature Engineering: Created rolling averages for the last 5 matches (xG, shots, shots on target), home/away indicators, and past performance against specific opponents.
✔ Normalization: Applied StandardScaler to standardize features before training.

2. Model Training: Bayesian Network

✔ Constructed a Bayesian Network representing team performance relationships.
✔ Estimated Conditional Probability Tables (CPTs) using Maximum Likelihood Estimation.
✔ Implemented inference using Variable Elimination to predict match outcomes.

3. Model Evaluation

✔ Generated a classification report with precision, recall, and F1-score.
✔ Examined the confusion matrix to evaluate misclassifications.
✔ Achieved an accuracy of 47.23%, with challenges in predicting draws (0% recall for draws).

Results & Analysis

Class

Precision

Recall

F1-Score

Support

Win (1)

0.46

0.71

0.56

1919

Draw (0)

0.00

0.00

0.00

1248

Loss (-1)

0.50

0.54

0.52

1905

Overall Accuracy



47.23%



Key Takeaways:

Wins and losses were somewhat predictable, but the model completely failed to classify draws.

Feature selection may need improvements, as current features might not capture the nuances of drawn matches.

Conditional Probability Tables (CPTs) may need adjustments, potentially increasing feature discretization bins.

Next Steps & Improvements

🔄 Run a Naïve Bayes Model for comparison.

🔧 Improve Feature Engineering (e.g., adding betting odds, team form factors).

📈 Tune Bayesian Network Hyperparameters (e.g., adjust discrete bins for CPTs).

🤖 Consider Other Probabilistic Models (e.g., Hidden Markov Models for sequential prediction).

📂 Files in Repository

File

Description

games.csv

Match-level statistics

teamstats.csv

Team-level performance metrics

shots.csv

Detailed shot data

football_predictor.ipynb

Jupyter Notebook containing the full implementation

processed_teamstats.csv

Preprocessed dataset used for model training

bayesian_network.png

Visualization of the Bayesian Network


🔗 References & Acknowledgments

Dataset Source: 
Chat GPT
