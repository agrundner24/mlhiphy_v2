# mlhiphy_v2

This repository builds upon and improves the work we did in https://github.com/ratnania/mlhiphy

Improvements include:

* A much more efficient and stable implementation of the negative log-likelihood. This vastly improves the algorithm, as the optimization of the negative log-likelihood is at its center. This was done by utilizing the block matrix structure of the covariance matrix and by using the Cholesky decomposition. See: [2D example](http://nbviewer.jupyter.org/github/Slowpuncher24/mlhiphy_v2/blob/master/2D_example.ipynb) or [3D example](http://nbviewer.jupyter.org/github/Slowpuncher24/mlhiphy_v2/blob/master/3D_example.ipynb)
* The inference of up to four hidden parameters in three dimensions, as opposed to one hidden parameter in two dimensions (respectively counting the temporal dimension as one). 
See: [without noise](http://nbviewer.jupyter.org/github/Slowpuncher24/mlhiphy_v2/blob/master/without_noise.ipynb)
* An alternative implementation of the negative log-likelihood for the noise-free case, where we can optimize over one hyperparameter less (the signal variance can be written in terms of other values).
* The implementation and tests of using the Matérn-5/2-kernel, which is the most promising alternative to the SE kernel.
* The implementation and tests of a viable alternative to the Nelder-Mead optimization algorithm, namely a variant of the nonlinear conjugate gradient method (it is scipy's implementation up to a minor tweak to the line search algorithm).

The performance of other popular optimization algorithms like LBFGS-B and stochastic gradient descent algorithms was tested but turned out to be deficient.
