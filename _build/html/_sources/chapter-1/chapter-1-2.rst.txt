1.2 Probability Theory
=====================================

Probability theory provides a consistent framework for the quantification and manipulation of uncertainty and forms one of the central foundations for pattern recognition.

  **The Rules of Probability**

  sum rule:
  
  .. math::
     p(X) = \sum_Y p(X, Y)
 
  product rule:
 
  .. math::
 
     p(X, Y) = p(Y \mid X)p(X)

From the product rule and the similarity property, we obatin the Bayes' theorem:

  **Bayes' Theorem**

  .. math::

     p(Y \mid X) = \frac{P(X \mid Y)p(Y)}{p(X)}

Two random variables :math:`X` and :math:`Y` are said to be independent if :math:`p(X, Y) = p(X)p(Y)`.
