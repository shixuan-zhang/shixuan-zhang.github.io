---
layout: archive
title: "Research"
permalink: /research/
author_profile: true
---

## Overview

Many optimization problems arising from pivotal applications, such as renewable energy operations, face tractability issues due to either of the following characteristics:
* large- or infinite-dimensional decisions, especially under uncertainty,
* lack of convexity in the objective or constraint functions.

My overarching goal is to provide theoretic and algorithmic insights for these challenging problems with practically efficient modeling and solution methods, by advancing in the following two directions:
* introduction of novel geometric perspectives (esp. convex, discrete, or algebraic geometry) to optimization theory,
* identification of problem-specific (e.g., combinatorial and statistical) structures, that allow improved efficiency compared with generic problems.


## Selected Works

### Mixed-integer Multistage Stochastic Optimization

When optimization decisions may adapt to a stochastic process, the problem size would generally grow exponentially with respect to the number of stages.
Thus a common solution algorithm for multistage stochastic optimization, called *Stochastic Dual Dynamic Programming* (SDDP), utilizes sampling and duality for nested approximation to reduce the computational effort in each iteration.

[Stochastic Dual Dynamic Programming for Multistage Stochastic Mixed-Integer Nonlinear Optimization](https://arxiv.org/abs/1912.13278)
* We show that SDDP can be extended to mixed-integer problems by replacing the usual convex duality with generalized conjugacy (or augmented Lagrangian duality with non-norm augmenting terms).
* The iteration complexity of such SDDP scales linearly with the number of stages in several practical situations, but may depend exponentially on the state space dimension in the worst-case analysis. 


### Finite Generation of Integer Points in Convex Cones

Integer points insides a rational polyhedral cone can be written as finite sums of a finite subset of integer points inside the cone, called a generating set.
The description and characterization of such generating sets are closely related to integer optimization via total dual integrality and cutting plane methods.

[Integer Points in Arbitrary Convex Cones: The Case of the PSD and SOC Cones](https://arxiv.org/html/2403.09927) 
* We extend the notion of finite generation of integer points to more general convex cones, e.g., cones of positive semidefinite matrices and second-order cones.
Finite generation is made possible on many such cones by considering a finitely generated unimodular action group (e.g., rotations and reflections of integer points).
* We also show that such finite generation is not always possible, even for irrational polyhedral cones in the plane.


### Sums of Squares and Low-rank Semidefinite Optimization

Semidefinite optimization has been widely adopted in many combinatorial and nonlinear optimization problems due to its modeling and approximation power.
However, the conventional interior-point methods for semidefinite optimization may not scale to large instances, and one popular alternative is to only consider low-rank positive semidefinite matrices to speed up the computation.

[Spurious local minima in nonconvex sum-of-squares optimization](https://arxiv.org/abs/2411.02208)
* We study spurious local minima (i.e., local minima that are not global) of low-rank methods from a sum-of-square perspective, and construct examples where spurious local minima persist with almost full rank.
* Further, we fully characterize the spurious local optima on the Veronese surface, which is an important object in real algebraic geometry, when we want to find a low-rank sum-of-square representation of a nonnegative polynomial.

