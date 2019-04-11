A Virtual Element Method for Resistive MHD.

The virtual element method(VEM) is a novel genearalization of the more classical
finite element method(FEM). It allows for great generality in the types of meshes
that are admissible. Therefore, the VEM method is perfectly suited for problems
with oddly shaped material interphases since the mesh can, most likely, be fitted
to the interphase.

The mimetic finite difference(MFD) method is a precursor of the VEM and shares 
many of the same features of the VEM with the difference that theoretical
analysis (say of stability and/or convergence) is significantly more complicated.
The VEM can, for the most part, take advantage of well-known results in the FEM
for its analysis greatly simplifying it.

My adviser and I, in collaboration with the Los Alamos National Laboratoty(LANL)
developed and implemented an MFD method for resistive MHD. However, in order to
publish the results we decided to pursue some stability analysis and the clearest
way to do this was to reframe into a VEM. We have obtained the analysis required 
in the VEM framework but a new complication arose: the MFD method we had implemented
and the VEM method we analysed are not the same method although the difference is
not very large it still implies that the implementation of the method needs to
be revised, and the convergence plots updated.

When I wrote the MFD method I knew only some rudimentary python and had never worked 
in a large coding project so the code that I do have is a mess, meaning that it is
disorganized and the implementation inefficient.

My project proposal has three goals:

1. Revise the MFD implementation and make the necessary changes into a VEM and obtain
the convergence plots.

2. Speed up the code maybe by parallelizing parts of it or otherwise.

3. Organize the code into packages that can be shared and utilized by anyone outside of
our group.

The code, as I currently have it, works as follows:

-The user provides the mesh, I used mathematica to create the meshes and developed
a package to import them into python and save them in a file that python can quickly
load along with important information regarding the cells like the barycenter and
orientation.

-Once the mesh is provided, the code runs from cell to cell computing local mass matrices
which then are assembled into global matrices.

-The final step is a time integration, here we must perform a linear solve at every time
step.

Finally, the packages that are currently being used are: numpy, math, pylab, pickle,
mpl_toolkits and scipy.

To our knowledge (my collaborators and I) there are no publications on development of
VEMs and MFD methods for MHD. However, the general theory of the design and analysis
of these can be found here:

For MFD

Lourenco Beirao da Veiga, Konstantin Lipnikov, and Gianmarco Manzini.The mimetic finite
difference method for elliptic problems, volume 11. Springer, 2014.

For VEM

Beirao da Veiga, Franco Brezzi, Luisa Donatella Marini, and Alessandro Russo.
The hitch-hiker’s guide to the virtual element method.Mathematical models and methods
in appliedsciences, 24(08):1541–1573, 2014.

L Beirao Da Veiga, Franco Brezzi, Luisa Donatella Marini, and Alessandro Russo. H(div)
and H(curl)-conforming vem.arXiv preprint arXiv:1407.6822, 2014.


