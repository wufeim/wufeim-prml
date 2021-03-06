1.1 Example: Polynomial Curve Fitting
=====================================

Suppose we observe a real-valued target variable :math:`x` and we wish to use this observation to predict the value of a real-valued target variable :math:`t`. We generate synthetic data from the function :math:`\sin(2 \pi x)` with random noise included in the target values. In real data sets, the noise may arise from intrinsically stochastic processes such as radioactive decay but more typically is due to there being sources of variability that are themselves unobserved.

Now suppose that we are given a training set comprising :math:`N` observations of :math:`x`, written :math:`\mathbf{x} \equiv (x_1, \dots, x_N)^\top`, together with corresponding observations of the values of :math:`t`, denoted :math:`\mathbf{t} = (t_1, \dots, t_N)`.

Consider a simple approach based on curve fitting. We fit the data using a polynomial function of the form

.. math::

   y(x, \mathbf{w}) = \sum_{j=0}^M w_jx^j

Functions, such as the polynomial, which are linear in the unknown parameters are called *linear models*. We minimize the error between the function :math:`y(x, \mathbf{w})` and the training data:

.. math::

   E(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^N \{ y(x_n, \mathbf{w}) - t_n \}^2

Since the :math:`E(\mathbf{w})` is a quadratic function of the coefficients :math:`\mathbf{w}`, we can find the closed form solution of :math:`\mathbf{w}` that minimizes :math:`E(\mathbf{w})`. There remains the problem of choosing the order :math:`M` of the polynomial and this is an example of *model comparison* or *model selection*. The figure below shows four examples of fitting polynomials with :math:`M = 0, 1, 3, 9` to the data set. We notice that :math:`M=0, 1` give rather poor fits to the data and consequently rather poor representations of the underlying function :math:`\sin(2\pi x)`, while :math:`M=9` obtain an excellent fit but oscillates wildly. The latter behaviour is known as *over-fitting*.

.. image:: figures/fig-1-1-1.png
   :height: 280pt

We shall evaluate :math:`\mathbf{w}^*` on a test data set from the same underlying distribution. It is sometimes more convenient to use the root-mean-square (RMS) error defined by

.. math::

   E_\text{RMS} = \sqrt{2E(\mathbf{w}^*)/N}

Graphs of the training data and test set RMS errors are shown for various values of :math:`M` in the figure below.

.. image:: figures/fig-1-1-2.png
   :height: 160pt

One technique that is often used to control the over-fitting phenomenon in such cases is that of *regularization*, which involves adding a penalty term to the error function in order to discourage the coefficients from reaching large values

.. math::

   \tilde{E}(\mathbf{w}) = \frac{1}{2} \sum_{n=1}^N \{ y(x_n, \mathbf{w}) - t_n \}^2 + \frac{\lambda}{2} \lVert \mathbf{w} \rVert_2^2

Note that the coefficient :math:`w_0` is omitted from the regularizer because its inclusion causes the results to depend on the choice of origin for the target variable, or it may be included but with its own regularization coefficient. Techniques such as this are known as *shrinkage* methods because they reduce the value of the coefficients. The particular case of a quadratic regularizer is called *ridge regression* and in neural networks, this is known as *weight decay*. The figure below shows the impact of the regularization term on the generalization error.

.. image:: figures/fig-1-1-3.png
   :height: 160pt
