# Upper Confidence Bound (UCB) – Ad Selection Optimization

## Project Overview

This project implements the **Upper Confidence Bound (UCB)** algorithm to solve an online advertising optimization problem using the Multi-Armed Bandit approach.

The objective is to identify which advertisement generates the highest user engagement by balancing two important strategies:

- **Exploration:** Testing different advertisements to gather information about their performance.
- **Exploitation:** Selecting advertisements that have already demonstrated higher reward rates.

Unlike traditional approaches that test all advertisements equally, UCB dynamically adjusts its selections based on previously observed rewards, aiming to maximize the total reward over time.

## Dataset

The project uses the `Ads_CTR_Optimisation.csv` dataset, which contains user interaction data for 10 different advertisements across 10,000 rounds.

- **Observations:** 10,000
- **Advertisements:** 10
- **Values:** Binary outcomes representing whether a user clicked on an advertisement.
  - `1`: The user clicked on the advertisement.
  - `0`: The user did not click on the advertisement.

Each row represents an interaction round, and each column corresponds to an advertisement.

## Technologies & Libraries

- Python
- NumPy
- Pandas
- Matplotlib
- Math

## Methodology

### 1. Data Loading

Imported the advertising dataset using Pandas to prepare the interaction data for the UCB algorithm.

### 2. UCB Algorithm Implementation

Implemented the Upper Confidence Bound algorithm from scratch to determine which advertisement should be selected at each round.

The algorithm evaluates each advertisement using an upper confidence bound calculated from:

- **Average Reward:** The observed average reward for each advertisement.
- **Confidence Interval:** An exploration term that accounts for the number of times each advertisement has been selected.

The upper confidence bound is calculated as:

\[
UCB_i = \bar{x}_i + \sqrt{\frac{3}{2}\frac{\ln(n+1)}{N_i}}
\]

Where:

- \(\bar{x}_i\): Average reward of advertisement \(i\).
- \(n\): Current round.
- \(N_i\): Number of times advertisement \(i\) has been selected.

Advertisements with no previous selections are initially assigned an extremely high upper bound, ensuring that every advertisement is explored before the algorithm begins favoring those with better observed performance.

### 3. Reward Optimization

The algorithm was executed over 10,000 rounds.

At each iteration, it:

1. Calculates the upper confidence bound for each advertisement.
2. Selects the advertisement with the highest upper confidence bound.
3. Observes the corresponding reward.
4. Updates the number of selections and cumulative rewards.
5. Repeats the process to improve future decisions.

### 4. Results Visualization

Used Matplotlib to create a histogram showing how frequently each advertisement was selected throughout the 10,000 rounds.

This visualization helps identify which advertisements the algorithm considers more promising based on their observed reward performance.

## Results

After 10,000 rounds, the selection distribution was:

| Advertisement | Number of Selections |
|---|---:|
| Ad 1 | 705 |
| Ad 2 | 387 |
| Ad 3 | 186 |
| Ad 4 | 345 |
| Ad 5 | 6,323 |
| Ad 6 | 150 |
| Ad 7 | 292 |
| Ad 8 | 1,170 |
| Ad 9 | 256 |
| Ad 10 | 186 |

**Key Finding:**

Advertisement 5 (index 4 in the dataset) was selected 6,323 times, representing approximately 63.23% of all selection rounds.

This indicates that the algorithm identified this advertisement as having a particularly promising reward rate and increasingly favored it as more interaction data became available.

## Key Takeaways

This project demonstrates the application of reinforcement learning concepts to advertising optimization and sequential decision-making.

Key concepts explored include:

- Multi-Armed Bandit problems.
- Upper Confidence Bound (UCB).
- Exploration vs. exploitation trade-off.
- Dynamic decision-making.
- Reward tracking and optimization.
- Data visualization using Matplotlib.

## Future Improvements

Potential improvements to explore:

- Implement and compare UCB with the Thompson Sampling algorithm.
- Compare cumulative rewards across different strategies.
- Evaluate the algorithm using different exploration parameters.
- Investigate how the number of rounds affects convergence.
- Explore applications in recommendation systems and personalized advertising.

## Author

**Isadora Caetano de Almeida**

[GitHub Profile](https://github.com/isadorafisica1512)
