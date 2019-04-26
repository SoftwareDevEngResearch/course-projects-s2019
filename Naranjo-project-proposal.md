An summation by parts method for acoustic wave propagation.

The goal of this project is to implement the finite difference method presented in the reference:

O'Reilly, O., Lundquist, T., Dunham, E. M., & Nordström, J. (2017). Energy stable and high-order-accurate finite difference methods on staggered grids. Journal of Computational Physics, 346, 572-589.

This method is a discretization of the classic wave equation written as a system of two first order equations.
It describes the behaviour of acoustic pulses.

The code has three main parts:

1. Meshing.
2. Constructing the finite difference operators.
3. Solving the system in a time integration.

The main complication in this method is constructing high order finite difference operators in space and time and ensuring 
the stability of the method. However, a method that is second order in space as well as time is relatively straight-forward from what I have read. My plan is to develop the implementation of the second order method, should time permit I will allow the user to choose the order (either 2 or 4).

The inputs from a usser would be the initial, boundary conditions, final time of the simulation and mesh parameters 
like space and time step sizes.

The packages that I expect to use are: numpy, math, pylab,
pickle, mpl_toolkits and scipy 
