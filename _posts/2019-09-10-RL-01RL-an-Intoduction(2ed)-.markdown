---
layout: post
title:  "Reinforcement Learning an Introduction - Richard S. Sutton (Highlight 01)"
date:   2019-09-10
categories: machine_learning
---
# Reinforcement Learning an Introduction - Richard S. Sutton (Highlight 01)

# Chapter 1. Introduction

# 1.1 Reinforcement Learning
Reinforcement learning is learning what to do - how to map situations to actions - so as to maximize a numerical reward signal.
<br>

Features of Reinforcement learning
- Trial and error
- delayed reward
<br>

Reinforcement is a problem, a class of solution methods that work well on the problem, and the field that studies this problem and its solution methods.
<br>

The distinction between problems and solution methods is very important in Reinforcement learning; failing to make this distinction is the source of many confutions.
<br>

We formailize the problem of reinforcement learning using ideas from dynamical systems theory, specifically, as the optimal control of incompletely-known Markov decision processes.
<br>

A learning agent must be able to sense the state of its environment to some extent and must be able to take actions that affect the state. The agent also must have a goal or goals relating to the state of the environment.
<br>

Markov decision processes are intended to include just these three aspects, sensation, action and goal.
<br>

- Supervised learning
- Unsupervised learning
- Reinforcement learning
<br>

One of the challenges that arise in reinforcement learning, and not in other kinds of learning, is the trade-off between exploration and exploitation.
<br>

The agent has to exploit what it has already experienced in order to obtain reward, but it also has to explore in order to make better action selections in the future.
<br>

Another key feature of reinforcement learning is that it explicitly considers the whole problem of a goal-directed agent interacting with an uncertain environment.
<br>

For learning research to make progress, important subproblems have to be isolated and studied, but they should be subproblems that play clear roles in complete,interactive, goal-seeking agents, even if all the details of the complete agent cannot yet be filled in.
<br>

Complete, interactive, goal-seeking agent we do not always mean something like a complete organism or robot. These are clearly examples, but a complete, interactive, goal-seeking agent can also be a component of a larger behaving system. In the case the agent directly interacts with the rest of the larger system and indirectly interacts with larger system's environment.
<br>

# 1.2 examples
Examples and possible applications
<br>

- chess
- To adjust parameters of a petroleum refinery's operation in real time
- A gazelle calf runs at 20 miles in half and hour after being born
- A mobile robot decides whether it should enter a new room in search of more trash to collect or start to find its way back to its battery recharging station.
- Phil's breakfast. Processes to have breakfast
<br>

All involve interaction between an active decision-making agent and its environment, within which the agent seeks to achieve a goal despite uncertainty about its environment.
<br>

The agent's actions are permitted to affect the future state of the environment, whereby affecting the action and opportunities available to the agent at later times.
<br>

At the same time, in all of those examples the effects of actions cannot be fully predicted, thus the agent must monitor its environment frequently and react appropliately.
<br>

In all of these examples the agent can use experience to imporve its performance over time.
