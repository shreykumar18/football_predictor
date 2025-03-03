# Football Match Prediction Using Bayesian Networks

## Project Overview

This project aims to develop a predictive model for football matches using Bayesian Networks. The goal is to analyze historical match data and predict match results and key in-game statistics such as expected goals (xG) and shots on target. The dataset used includes detailed match and team statistics, allowing for pattern recognition and probabilistic modeling.

## Dataset

The dataset includes the following files:
- `games.csv`: Information on matches, including teams, scores, and betting odds.
- `teamstats.csv`: Detailed team statistics per match.
- `shots.csv`: Shot-level data, including player actions.
- `teams.csv`: Team identifiers and metadata.
- `players.csv`: Player identifiers and metadata.
- `appearances.csv`: Player appearances in matches.

## AI Agent Design

The AI agent is structured as a **goal-based agent** with the following components:

- **Performance Measure**: The accuracy of predicting match results and statistical outcomes.
- **Environment**: Match data, historical results, and team performance statistics.
- **Sensors**: Features such as xG, possession, shots on target, past performance, and match location.
- **Actuators**: The agent generates probability distributions for outcomes based on Bayesian inference.

## Data Preprocessing

1. **Handling Missing Values**  
   - Categorical missing values were filled with `"Unknown"`.
   - Numerical missing values were filled with the median.
   - `assisterID` in `shots.csv` was filled with `0` for missing values.

2. **Feature Engineering**  
   - Created rolling averages for the last 5 matches (`xGoals_rolling5`, `shots_rolling5`, `shotsOnTarget_rolling5`).
   - Derived home/away performance indicators.
   - Aggregated past performance against opponents.

3. **Discretization**  
   - Continuous features were discretized using `KBinsDiscretizer` to enable probabilistic reasoning in the Bayesian Network.

## Model: Bayesian Network

A Bayesian Network was constructed with nodes representing key features such as:
- `xGoals_rolling5`
- `shotsOnTarget_rolling5`
- `is_home`
- `result` (match outcome)

### Training and Inference
- The network structure was defined based on domain knowledge.
- Conditional Probability Tables (CPTs) were estimated using Maximum Likelihood Estimation.
- Inference was performed using Variable Elimination.

## Results

| Metric        | Score |
|--------------|-------|
| Accuracy     | 47.2% |
| Precision (-1, 0, 1) | 0.50, 0.00, 0.46 |
| Recall (-1, 0, 1) | 0.54, 0.00, 0.71 |
| F1-Score (-1, 0, 1) | 0.52, 0.00, 0.56 |

The confusion matrix showed that the model struggled with predicting draws (`0` result) and had mixed performance on wins and losses.

## Future Improvements

1. **Feature Selection**  
   - Include additional statistics like pass accuracy, defensive metrics, and possession changes.
   
2. **Alternative Models**  
   - Compare the Bayesian Network with other probabilistic models (e.g., Hidden Markov Models).
   - Implement machine learning classifiers like Random Forest or Neural Networks.

3. **Parameter Tuning**  
   - Optimize discretization strategies for better binning of continuous features.
   - Adjust Bayesian Network structure based on domain insights.
  

## Citations

1. [Football Database - Kaggle](https://www.kaggle.com/datasets/technika148/football-database?resource=download)
2. Chat GPT
3. This project utilizes the pgmpy library for Bayesian Networks. 



## Conclusion

This project demonstrates how Bayesian Networks can be applied to football match prediction. Although the current model has limitations, it provides insights into match outcomes based on team statistics. Future work will involve refining feature selection and comparing different models for better accuracy.
