---
layout: page
title: Notes on Optimization
---
Optimization can be understood as the minization of an arbitrary function. To apply this methodology onto the problem at hand, the problem has to be converted into a function that is able to represent the problem.

# Problem formulation

-	What is the optimal objective function that represents the quasi-stationary state of the hatch ? (Does a constant value fit the description of the quasi-stationary state)
- How does an appropriate transition function from molten to powder areas at the boundary of the hatch need to be designed? (Is a discrete transition sufficient, or does a continous smooth transition function better represent the actual physics due to the gaussian beam shape.)

Does the exact design of the objective function play a role for the overall minimization process, or do they only shift the achieveable function values towards higher values ?

> Does a better representation of the problem lead to faster convergence of the optimization algorithm?


# Optimization Variables

The design space (search space) is defined by values for each subsequent hatch lines until the quasi-stationary state is reached. Combinations of variations are also possible

-	Power (Hard to adapt with the current hardware, since the changes in beam power do take time ~200ms)
- Velocity (Easily adaptable with the current hardware)
- Line Offset (Easily adaptable with the current hardware)
- Focus (The adaption of the focus for subsequent hatch lines should not yield a perfect edge, without the combination with the line offset)


> What combination of variables is able to reproduce the thermal history (meltpool geometry, thermal circle and solidification conditions) of the quasi-stationary state ?

An additional Question is how the solutions of the optimization proceedure can be generalized over the process parameter space, since each quasi-stationary state is different and is a function of the processing parameters.

# Meta
These questions concern the general optimization and the algorithms used to solve this problem (which are separated from the underlying physics of the problem)

- What kind of optimization algorithms are suited for such problems? (Different forms of optimization algorithms exist: Gradient based methods use the local gradient to predict the next potential solutin; Gradient-Free Methods are mostly stochastic methods that do not need the local graident)
- What are the limitations imposed by the problem description?(Black Box Optimization without gradient information and high evaluation times)
- What does the optimization landscape look like? (smooth vs. many local minima)
- What kind of internal parameters do benefit the convergence rate of the optimization alorithm?
- How does the starting point of the optimization influence the final outcome ?


