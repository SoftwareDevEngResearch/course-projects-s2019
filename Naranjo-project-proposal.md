An FDTD method for electromagnetic wave propagation in Linear/Non-linear media.

The goal of this project is to implement the finite difference time domain
method presented in the reference:

Brio, M., Caputo, J. G., Gwirtz, K., Liu, J., & Maimistov, A. (2019).
Scattering of a short electromagnetic pulse from a Lorentz-Duffing film:
theoretical and numerical analysis. Wave Motion.

This method is a discretization of the duffing model which describes the 
behaviour of electromagnetic pulses as they propagate in a medium where the
index of refraction changes as a response to the presence of an electric field.
Mathematically this is reflected on a non-linearity in the equation that 
describes the polarization of the material. 

The code has three main parts:

1. Meshing.
2. Constructing the finite difference operators.
3. Solving the system.

Due to the non-linearity solving the system requires implementing a Newton 
iteration or a fixed point iteration. Picking the parameters that guarantee
convergence may be a non-trivial task and my time is limited. Therefore, my 
first attempt will ignore the non-linear term completely, if this task is 
simpler than I expect then I will go back and reintroduce the non-linear term.

The packages that I expect to use are: numpy, math, pylab,
pickle, mpl_toolkits and scipy 
