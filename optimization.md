---
layout: page
title: Notes on Optimization
---

Optimization can be understood as the minization of an arbitrary function. To apply this methodology onto the problem at hand, the problem has to be converted into a  function that represents the problem.

-	What is the optimal objective function that represents the quasi-stationary state of the hatch? Does a constant value fit the description of the quasi-stationary state, or does the function need to be adapted?
- How does the appropriate transition function from molten to powder areas at the boundary of the hatch need to be desinged? Is a discrete transition sufficent, or does a continous smooth transition function better represent the actual physics (Gaussian Beam)

Do the above points play a role for the minimization itself, or do they only shift the achieveable functions values towards higher values? Does a better representation of the problem lead to faster convergence of the optimization algorithm?

Optimization Variables (Each variable can be varied for subsequent hatch lines until the quasi-stationary state is reached. Combinations of variations are also possible)

-	Power
-	Velocity
- Line Offset
- Focus (Different Beam Diameter)

What combination of variables is able to reproduce the thermal history (meltpool geometry, thermal circle, solidification conditions) of the quasi-stationary state ?

How can the solutions of the optimization proceedure be generalized over the necessary parameter space?

### Meta
The meta questions are aimed at the general optimization and the algorithm used to solve this problem and are seperate from the underlying physics of the problem.

- What kind of optimization algorithm is suited for this kind of problems? (Different forms of optimization algorithms exist: Gradient based methods use the local gradient to predict the next potential solutin; Gradient-Free Methods are mostly stochastic methods that do not need the local graident.)
- What are the limitations imposed by the problem description?(Black Box Optimization without gradient information and high evaluation times)
- What does the optimization landscape look like? (smooth vs. many local minima)
- What kind of internal parameters do benefit the convergence rate of the optimization alorithm?
- How does the starting point of the optimization influence the final outcome ?


