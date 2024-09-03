---
title: Improving Sarsa(λ) with Modified Eligibility Traces
date: 2021-01-01
tags:
  - Reinforcement Learning
featured: true
image:
  caption: "Created by OpenAI's DALL·E"
  focal_point: ""
  preview_only: false
---

Enhancing Sarsa(λ) algorithm performance with modified eligibility traces for effective exploration in Reinforcement Learning.

<!--more-->

## Introduction

In this project, we explored the relationship between exploration strategies and eligibility traces in reinforcement learning (RL), particularly focusing on the Sarsa(λ) algorithm. Our curiosity was driven by the potential impact of exploration on the agent's ability to remember past states and make optimal decisions. Eligibility traces allow an agent to keep a record of previously visited states and influences its future decisions. However, exploration, especially with random actions, can negatively affect this process, potentially leading to suboptimal performance. Our hypothesis was that exploration could degrade the performance of Sarsa(λ), and we sought to test this by experimenting with modifications to the trace updating method inspired by Watkins’s Q(λ) algorithm.

## Problem Definition

We used the Mountain Car problem, as introduced by Moore (1990), as our RL environment. This problem involves a car that must navigate a steep hill to reach a goal at the peak. The challenge lies in the car’s inability to ascend the hill directly due to insufficient engine power, requiring it to first move away from the goal to gain momentum. This scenario is a classic example in RL, where agents must learn to make decisions that may initially seem counterproductive but are necessary for long-term success. The task's state space is continuous and two-dimensional, requiring a function approximator for effective learning. We used Tile Coding, as suggested by Sutton and Barto (2018), to approximate the state space with overlapping tiles, simplifying the problem for the agent.

## Methodology

### Sarsa(λ) and ε-Greedy Policy

Our approach utilized the Sarsa(λ) algorithm, a temporal-difference (TD) learning method that balances the bias-variance trade-off through a parameter λ. Sarsa(λ) estimates the action-value function (Q(s, a)) for the current policy π, guiding the agent's decisions based on past experience. To encourage exploration and prevent the agent from settling on a suboptimal policy, we implemented an ε-greedy policy. This policy allows the agent to occasionally choose random actions, promoting exploration of the state space, even if it means sometimes selecting non-optimal actions. By adjusting ε, we controlled the frequency of random actions, thereby influencing the agent's exploration behavior.

### Eligibility Traces and Watkins’s Q(λ)

Eligibility traces provide a mechanism for integrating short-term memory into the agent’s learning process, maintaining a decaying record of previously visited states. This technique blends the strengths of temporal-difference learning and Monte Carlo methods, creating a spectrum where the parameter λ controls the trace's persistence. However, when the agent takes random actions, traditional eligibility traces can become problematic. Inspired by Watkins’s Q(λ) method, which sets the trace to zero after a random action, we modified the trace updating process in Sarsa(λ). This modification aimed to prevent random actions from skewing the learning process by effectively resetting the agent's memory after such actions, ensuring that only relevant state-action pairs influence future decisions.

## Experimental Setup

We conducted two main experiments to evaluate our hypotheses. The first compared the performance of Sarsa(λ) with a deterministic policy against a stochastic one, using the traditional trace updating method. The second experiment tested our modified trace updating method against the standard approach within Sarsa(λ). To optimize hyperparameters, we ran preliminary tests with varying values of λ and α, averaging results over multiple episodes and runs to identify the best-performing configurations.

## Results and Discussion

### Exploration and Sarsa(λ)

Our experiments confirmed that the performance of a stochastic policy, where the agent takes random actions (ε-greedy), is generally worse than a deterministic policy within the Sarsa(λ) framework. As shown in our results, increasing the value of ε led to a wider gap between the performance of deterministic and stochastic policies. This outcome aligns with our initial hypothesis that exploration could negatively impact the agent's ability to learn effectively from its past actions, especially in tasks requiring precise control like the Mountain Car problem.

### Improving the Performance of ε-Greedy Policy in Sarsa(λ)

Applying the concept from Watkins’s Q(λ) to Sarsa(λ), we introduced a new method for updating eligibility traces that resets the entire trace vector to zero after any random action. This approach effectively isolates the impact of exploratory actions, preventing them from corrupting the agent's learning based on prior states. Our results showed that this new trace updating method significantly improved the performance of the ε-greedy policy. As ε increased, the difference in performance between our new method and the standard one also grew, indicating that our approach is particularly beneficial in environments with higher exploration rates.

## Conclusion

This research demonstrated that while exploration is crucial for avoiding local optima, it can also hinder learning when using traditional eligibility traces in Sarsa(λ). By resetting the eligibility trace after random actions, inspired by Watkins’s Q(λ), we were able to mitigate some of the negative effects of exploration. Our modified Sarsa(λ) algorithm consistently outperformed the original version, particularly in scenarios with higher exploration rates. This suggests that integrating mechanisms to manage the impact of exploration can enhance the effectiveness of reinforcement learning algorithms in complex, continuous state spaces like the Mountain Car problem. Future work could explore the applicability of this approach to other domains and more complex tasks.

## References
- Andrew Moore. 1990. Efficient Memory-based Learning for Robot Control. Pittsburgh, PA.
- Richard S. Sutton and Andrew G. Barto. 2018. Reinforcement Learning: An Introduction. A Bradford Book, Cambridge, MA, USA.