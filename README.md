# Reinforcement Learning and the Racetrack Problem

## Authors: 
Benjamin Heinze, Braxton McCormack  
CSCI 446 — Artificial Intelligence, Project #4

## Project Overview:
This project implements reinforcement learning algorithms to solve the racetrack problem, a time-trial scenario where an agent controls a race car on a pre-defined track, attempting to minimize the time to cross the finish line. The problem is modeled using kinematic equations with discrete time steps, and reinforcement learning techniques such as Value Iteration, Q-learning, and SARSA are applied to optimize the car's movements.

## Key Components:
- **Racetrack Problem**: The car moves along a grid-based track with controlled acceleration in the x and y directions. Non-determinism is introduced, where 20% of acceleration attempts fail, simulating real-world uncertainty.
- **State Variables**: At each time step, the state of the car is represented by its x, y position and velocity in both directions. The agent controls the x and y accelerations.
- **Crash Handling**: Two variants are implemented to handle crashes: (1) reset the car to the nearest position on the track, and (2) reset the car to the starting position.
- **Cost Function**: The cost of each move is 1, while crossing the finish line has a cost of 0. The goal is to minimize the total cost, i.e., complete the race in the fewest steps possible.

## Problem Statement:
The goal is to apply reinforcement learning techniques to solve the racetrack problem by controlling the car's acceleration, deceleration, and turning on various tracks. The challenge includes accounting for non-determinism in acceleration and ensuring the car stays on track without crashing. The hypothesis is that Q-learning and SARSA, which are model-free learning methods, will perform better in handling non-determinism compared to Value Iteration, which is a model-based approach.

## Hypothesis:
It is expected that Q-learning and SARSA will adapt better to the randomness of the problem and find more optimal strategies over time. Value Iteration, being model-based, might converge faster but will struggle with handling the stochastic elements introduced by the 20% chance of failed acceleration.

## Experimental Approach:
- **Tracks**: The car is tested on four racetracks provided in the project files (L-track, O-track, R-track, and W-track). Each track is represented by a grid with different types of cells (starting line, finish line, racetrack, and walls).
- **Algorithms**: The following algorithms are implemented:
  - **Value Iteration**: Updates value functions iteratively using a model of the environment.
  - **Q-learning**: A model-free reinforcement learning method that updates Q-values based on observed rewards.
  - **SARSA**: Similar to Q-learning but updates Q-values based on the state-action pair of the next step.
- **Performance Metrics**: The algorithms are evaluated based on the number of training iterations and the number of steps the race car takes to reach the finish line. Learning curves are generated to visualize the performance.

## Results:
- **Value Iteration**: Converged to an optimal policy but struggled with the non-determinism, leading to longer training times.
- **Q-learning**: Showed faster adaptation to the randomness in the problem, but required extensive exploration to avoid local optima.
- **SARSA**: Performed similarly to Q-learning but was slightly more conservative in its exploration due to its on-policy nature.

## Discussion:
- **Crash Handling**: The harsher crash variant (resetting to the start) significantly increased the time to convergence, while the softer variant (resetting to the nearest position) allowed for quicker learning.
- **Exploration vs. Exploitation**: Both Q-learning and SARSA benefited from careful tuning of exploration parameters to balance learning and exploitation.
- **Learning Curves**: Q-learning and SARSA displayed smoother convergence compared to Value Iteration, particularly on tracks with more obstacles.

## Summary:
Reinforcement learning algorithms like Q-learning and SARSA are well-suited to handling the stochastic elements of the racetrack problem. Value Iteration, though theoretically optimal, struggled with the randomness and required more time to converge. The choice of crash handling and careful tuning of learning parameters played a significant role in the performance of the algorithms across different tracks.

## References:
- [Bresenham’s Line Algorithm](https://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm)
- JMLR Formatting Guide: [JMLR Format](http://www.jmlr.org/format/format.html)
