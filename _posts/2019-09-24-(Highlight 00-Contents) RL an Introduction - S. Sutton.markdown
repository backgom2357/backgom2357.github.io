---
layout: post
title: 'Highlight00 - Contents <br> [RL an Introduction - S. Sutton]'
date: 2019-09-24
categories: machine_learning
image: images/RLIntroduction_Sutton.png
tag: RLIntroduction
---

# Reinforcement Learning an Introduction - Richard S. Sutton

## Contents

#### 1 Introduction 1
1.1 Reinforcement Learning<br>
1.2 Examples<br>
1.3 Elements of Reinforcement Learning<br>
1.4 Limitations and Scope<br>
1.5 An Extended Example: Tic-Tac-Toe<br>
1.6 Summary<br>
1.7 Early History of Reinforcement Learning<br>

### I Tabular Solution Methods
#### 2 Multi-armed Bandits
2.1 A k-armed Bandit Problem<br>
2.2 Action-value Methods<br>
2.3 The 10-armed Testbed<br>
2.4 Incremental Implementation<br>
2.5 Tracking a Nonstationary Problem<br>
2.6 Optimistic Initial Values<br>
2.7 Upper-Confidence-Bound Action Selection<br>
2.8 Gradient Bandit Algorithms<br>
2.9 Associative Search (Contextual Bandits)<br>
2.10 Summary<br>

#### 3 Finite Markov Decision Processes
3.1 The Agent–Environment Interface<br>
3.2 Goals and Rewards<br>
3.3 Returns and Episodes<br>
3.4 Unified Notation for Episodic and Continuing Tasks<br>
3.5 Policies and Value Functions<br>
3.6 Optimal Policies and Optimal Value Functions<br>
3.7 Optimality and Approximation<br>
3.8 Summary<br>

#### 4 Dynamic Programming
4.1 Policy Evaluation (Prediction)<br>
4.2 Policy Improvement<br>
4.3 Policy Iteration<br>
4.4 Value Iteration<br>
4.5 Asynchronous Dynamic Programming<br>
4.6 Generalized Policy Iteration<br>
4.7 Efficiency of Dynamic Programming<br>
4.8 Summary

#### 5 Monte Carlo Methods
5.1 Monte Carlo Prediction<br>
5.2 Monte Carlo Estimation of Action Values<br>
5.3 Monte Carlo Control<br>
5.4 Monte Carlo Control without Exploring Starts<br>
5.5 Off-policy Prediction via Importance Sampling<br>
5.6 Incremental Implementation<br>
5.7 Off-policy Monte Carlo Control<br>
5.8 \*Discounting-aware Importance Sampling<br>
5.9 \*Per-decision Importance Sampling<br>
5.10 Summary<br>

#### 6 Temporal-Difference Learning
6.1 TD Prediction<br>
6.2 Advantages of TD Prediction Methods<br>
6.3 Optimality of TD(0)<br>
6.4 Sarsa: On-policy TD Control<br>
6.5 Q-learning: Off-policy TD Control<br>
6.6 Expected Sarsa<br>
6.7 Maximization Bias and Double Learning<br>
6.8 Games, Afterstates, and Other Special Cases<br>
6.9 Summary<br>

#### 7 n-step Bootstrapping
7.1 n-step TD Prediction<br>
7.2 n-step Sarsa<br>
7.3 n-step Off-policy Learning<br>
7.4 \*Per-decision Methods with Control Variates<br>
7.5 O↵-policy Learning Without Importance Sampling: The n-step Tree Backup Algorithm<br>
7.6 \*A Unifying Algorithm: n-step Q(σ)<br>
7.7 Summary<br>

#### 8 Planning and Learning with Tabular Methods
8.1 Models and Planning<br>
8.2 Dyna: Integrated Planning, Acting, and Learning<br>
8.3 When the Model Is Wrong <br>
8.4 Prioritized Sweeping <br>
8.5 Expected vs. Sample Updates <br>
8.6 Trajectory Sampling <br>
8.7 Real-time Dynamic Programming <br>
8.8 Planning at Decision Time <br>
8.9 Heuristic Search <br>
8.10 Rollout Algorithms<br>
8.11 Monte Carlo Tree Search<br>
8.12 Summary of the Chapter <br>
8.13 Summary of Part I: Dimensions<br>

### II Approximate Solution Methods
#### 9 On-policy Prediction with Approximation
9.1 Value-function Approximation <br>
9.2 The Prediction Objective (VE)<br>
9.3 Stochastic-gradient and Semi-gradient Methods<br>
9.4 Linear Methods <br>
9.5 Feature Construction for Linear Methods<br>
  9.5.1 Polynomials <br>
  9.5.2 Fourier Basis <br>
  9.5.3 Coarse Coding <br>
  9.5.4 Tile Coding <br>
  9.5.5 Radial Basis Functions <br>
9.6 Selecting Step-Size Parameters Manually <br>
9.7 Nonlinear Function Approximation: Artificial Neural Networks<br>
9.8 Least-Squares TD<br>
9.9 Memory-based Function Approximation <br>
9.10 Kernel-based Function Approximation<br>
9.11 Looking Deeper at On-policy Learning: Interest and Emphasis<br>
9.12 Summary <br>

#### 10 On-policy Control with Approximation
10.1 Episodic Semi-gradient Control<br>
10.2 Semi-gradient n-step Sarsa<br>
10.3 Average Reward: A New Problem Setting for Continuing Tasks<br>
10.4 Deprecating the Discounted Setting<br>
10.5 Di↵erential Semi-gradient n-step Sarsa<br>
10.6 Summary <br>

#### 11 \*Off-policy Methods with Approximation
11.1 Semi-gradient Methods <br>
11.2 Examples of Off-policy Divergence<br>
11.3 The Deadly Triad<br>
11.4 Linear Value-function Geometry<br>
11.5 Gradient Descent in the Bellman Error<br>
11.6 The Bellman Error is Not Learnable<br>
11.7 Gradient-TD Methods <br>
11.8 Emphatic-TD Methods<br>
11.9 Reducing Variance<br>
11.10 Summary<br><br>

#### 12 Eligibility Traces
12.1 The λ-return<br>
12.2 TD(λ)<br>
12.3 n-step Truncated λ-return Methods<br>
12.4 Redoing Updates: Online λ-return Algorithm<br>
12.5 True Online TD(λ)<br>
12.6 \*Dutch Traces in Monte Carlo Learning<br>
12.7 Sarsa(λ)<br>
12.8 Variable λ and γ<br>
12.9 \*Off-policy Traces with Control Variates<br>
12.10 Watkins’s Q(λ) to Tree-Backup(λ)<br>
12.11 Stable O↵-policy Methods with Traces<br>
12.12 Implementation Issues<br>
12.13 Conclusions<br>

#### 13 Policy Gradient Methods
13.1 Policy Approximation and its Advantages<br>
13.2 The Policy Gradient Theorem<br>
13.3 REINFORCE: Monte Carlo Policy Gradient<br>
13.4 REINFORCE with Baseline<br>
13.5 Actor–Critic Methods<br>
13.6 Policy Gradient for Continuing Problems<br>
13.7 Policy Parameterization for Continuous Actions<br>
13.8 Summary<br>

### III Looking Deeper
#### 14 Psychology
14.1 Prediction and Control<br>
14.2 Classical Conditioning<br>
  14.2.1 Blocking and Higher-order Conditioning<br>
  14.2.2 The Rescorla–Wagner Model<br>
  14.2.3 The TD Model<br>
  14.2.4 TD Model Simulations<br>
14.3 Instrumental Conditioning <br>
14.4 Delayed Reinforcement<br>
14.5 Cognitive Maps<br>
14.6 Habitual and Goal-directed Behavior<br>
14.7 Summary<br>

#### 15 Neuroscience
15.1 Neuroscience Basics<br>
15.2 Reward Signals, Reinforcement Signals, Values, and Prediction Errors<br>
15.3 The Reward Prediction Error Hypothesis<br>
15.4 Dopamine<br>
15.5 Experimental Support for the Reward Prediction Error Hypothesis<br>
15.6 TD Error/Dopamine Correspondence<br>
15.7 Neural Actor–Critic<br>
15.8 Actor and Critic Learning Rules<br>
15.9 Hedonistic Neurons<br>
15.10 Collective Reinforcement Learning<br>
15.11 Model-based Methods in the Brain<br>
15.12 Addiction <br>
15.13 Summary<br>

#### 16 Applications and Case Studies
16.1 TD-Gammon<br>
16.2 Samuel’s Checkers Player<br>
16.3 Watson’s Daily-Double Wagering<br>
16.4 Optimizing Memory Control<br>
16.5 Human-level Video Game Play<br>
16.6 Mastering the Game of Go<br>
16.6.1 AlphaGo<br>
16.6.2 AlphaGo Zero<br>
16.7 Personalized Web Services<br>
16.8 Thermal Soaring<br>

#### 17 Frontiers
17.1 General Value Functions and Auxiliary Tasks<br>
17.2 Temporal Abstraction via Options<br>
17.3 Observations and State<br>
17.4 Designing Reward Signals<br>
17.5 Remaining Issues<br>
17.6 The Future of Artificial Intelligence<br>
