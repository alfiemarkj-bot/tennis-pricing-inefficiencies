# Analyzing Pricing Inefficiencies in Professional Tennis Match Odds
## A Data-Driven Comparison of Model-Based and Market-Implied Probabilities
# Project Overview

This project investigates how accurately bookmaker odds reflect the true probability of match outcomes in professional men’s tennis. Using historical ATP match data and publicly available betting odds, I compare bookmaker-implied probabilities with probabilities estimated from a simple data-driven model.

The goal of the project is not to develop a betting system, but to apply probabilistic modeling, feature engineering, and calibration analysis to understand how well betting markets align with historical outcomes. The analysis focuses on probability calibration rather than prediction accuracy, providing insight into where markets perform strongly and where uncertainty is greatest.

## Research Question

How accurately do bookmaker odds reflect the true probability of match outcomes in professional tennis, and can historical match data identify systematic differences between market-implied and model-based probabilities?

## Data Sources
Match Data

Source: Jeff Sackmann’s Tennis ATP dataset

Coverage: 2024 ATP men’s singles matches

Contents: Match outcomes, tournament context, player rankings, ranking points, age, surface, and match statistics

Betting Odds

Source: Public bookmaker odds dataset

Bookmaker used: Bet365

Odds format: Decimal odds for match winner and loser

## Methodology
### Data Preparation

Match-level data was transformed into a player–opponent (long) format, where each row represents a single player’s perspective in a match.

A binary outcome variable (win) indicates whether the player won the match.

Feature engineering included:

Ranking difference

Ranking points difference

Age difference

Height difference

## Baseline Probability Model

A logistic regression model was trained to estimate the probability that a player wins a match.

### Features used:

Ranking difference

Ranking points difference

Age difference

The model was trained using a train/test split to ensure out-of-sample evaluation.

### Market-Implied Probabilities

Bookmaker odds were converted to implied probabilities using:

p = 1 / decimal odds

Both winning and losing sides of each match were included to create a balanced probability distribution.

## Evaluation via Calibration

Rather than focusing on accuracy or returns, model performance was evaluated using probability calibration:

Predicted probabilities were grouped into bins.

For each bin, the average predicted probability was compared to the observed win rate.

Calibration curves were constructed for:

The data-driven model

Bookmaker-implied probabilities

## Key Results
Overall Calibration: Model vs Market

Both the logistic regression model and bookmaker-implied probabilities demonstrate strong overall calibration, with observed win rates closely tracking predicted probabilities across most probability ranges.

The betting market performs particularly well at extreme probabilities (strong favourites).

The data-driven model achieves competitive calibration in mid-range probabilities despite using only publicly available historical features.

### Favourite vs Underdog Analysis

To examine whether calibration differs by market expectation, predicted probabilities were segmented into:

Favourites: predicted probability ≥ 0.5

Underdogs: predicted probability < 0.5

### Findings

#### Favourites

Both the model and the market are well calibrated.

The market is especially strong for heavy favourites, likely reflecting expert judgment and contextual factors not captured by the model.

#### Underdogs

Calibration is weaker for both approaches, reflecting greater outcome volatility.

The data-driven model shows slightly improved calibration in moderate underdog ranges, suggesting historical performance data may partially correct market pessimism.

## Interpretation

The betting market is most efficient where information is most certain, while data-driven models remain competitive in more uncertain regions of the probability spectrum. This highlights both the strength of market pricing and the value of structured historical data in probabilistic analysis.

## Limitations

The model uses a limited set of features and does not account for:

Injuries

Recent form

Head-to-head matchups

Detailed surface-specific performance

Odds and match data were not merged at an exact match level due to identifier inconsistencies; comparisons are performed at the distribution and calibration level.

The analysis does not account for bookmaker margins or market dynamics over time.

## Future Work

Potential extensions include:

Surface-specific models (hard, clay, grass)

Time-weighted or rolling performance metrics

Tournament-level or round-level segmentation

Incorporating additional public features such as recent form or head-to-head statistics

Formal calibration metrics (Brier score, log loss)

## Ethical Note

This project is intended for educational and analytical purposes only. It does not promote gambling behaviour or provide betting advice. All conclusions are framed in terms of probability estimation and market efficiency analysis.

## Technologies Used

Python

pandas

NumPy

scikit-learn

matplotlib

Jupyter Notebook

## Author

### Alfie Johnson
