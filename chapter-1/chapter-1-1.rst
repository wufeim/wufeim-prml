1.1 Example: Polynomial Curve Fitting
=====================================

Suppose we observe a real-valued target variable :math:`x` and we wish to use this observation to predict the value of a real-valued target variable :math:`t`. We generate synthetic data from the function :math:`\sin(2 \pi x)` with random noise included in the target values. In real data sets, the noise may arise from intrinsically stochastic processes such as radioactive decay but more typically is due to there being sources of variability that are themselves unobserved.

Now suppose that we are given a training set comprising :math:`N` observations of :math:`x`, written :math:`\mathbf{x} \equiv (x_1, \dots, x_N)^\top`, together with corresponding observations of the values of :math:`t`, denoted :math:`\mathbf{t} = (t_1, \dots, t_N)`.
