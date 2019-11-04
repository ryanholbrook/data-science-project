
# Table of Contents

1.  [Process](#orga84d9db)
2.  [Objectives](#org01d91e3)
3.  [Data Collection](#orgb8f9904)
    1.  [Experimental Design](#orgc7a180e)
4.  [Data Specification](#orgec6575a)
    1.  [Determine Statistical Type](#org091b506)
    2.  [Determine Roles](#orgf087bca)
    3.  [Determine Validation Rules](#org02aa625)
5.  [Data Correction](#orga9f8c95)
    1.  [String Correction](#org939dca6)
    2.  [Numeric Correction](#orgfba8b3a)
    3.  [Missing Correction](#org42b5553)
6.  [Determine Model Validation Scheme](#orgf073b3d)
7.  [Establish Baseline Performance and Evaluation Metrics](#org750f50a)
8.  [Feature Engineering and Model Selection](#orgbe482f7)
9.  [Training and Tuning](#orgf51ed2c)
10. [Model Evaluation](#org5c8369b)
11. [Model Interpretation](#org97f16bd)
12. [Reporting and Deployment](#orgeb66f31)
13. [References](#orgc2b733a)



<a id="orga84d9db"></a>

# Process


<a id="org01d91e3"></a>

# Objectives

Understand utilities. What are the costs of erroneous predictions? What are the benefits of correct predictions? This should (help) determine your scoring function.

Determine Constraints. Do you want predictions? Does the model need to be interpretable? What resources do you have?

Define success. How do you know you're done?


<a id="orgb8f9904"></a>

# Data Collection

Collect the data in raw form, if not provided.


<a id="orgc7a180e"></a>

## Experimental Design

Statistically optimal ways of collecting data. The mantra is: *To get the most from your experiments, reduce the variance.* (Good 2005) When data collection is expensive, try to do it in the best way possible. Can be used for computer simulations, too. Consider active learning if you need to label data.


<a id="orgec6575a"></a>

# Data Specification

Determine what properties the data should have.


<a id="org091b506"></a>

## Determine Statistical Type

-   Binary: Integer or Logical
-   Nominal: Factor
-   Ordinal: Ordered Factor
-   Continuous: Float
-   Linear Temporal: Date
-   Cyclic Temporal: Factor
-   Text: String

See [Statistical Data Type](https://en.wikipedia.org/wiki/Statistical_data_type) [Wikipedia]


<a id="orgf087bca"></a>

## Determine Roles

-   Feature
-   Response
-   Identity
-   Information


<a id="org02aa625"></a>

## Determine Validation Rules

Specify what properties the data must have to be "clean". Domain knowledge is essential here.


<a id="orga9f8c95"></a>

# Data Correction

Decide on how to correct erroneous data. Understanding why the data is erroneous is important. Visualization tools can help.

Many errors can be corrected through an automatic application of rules. For others, error localization can be used to remove any uncorrectable fields.

Correct observed data before imputing missing data.


<a id="org939dca6"></a>

## String Correction


<a id="orgfba8b3a"></a>

## Numeric Correction


<a id="org42b5553"></a>

## Missing Correction


<a id="orgf073b3d"></a>

# Determine Model Validation Scheme

Decide on validation procedures (for feature engineering, performance, tuning, benchmarking) and make data splits.


<a id="org750f50a"></a>

# Establish Baseline Performance and Evaluation Metrics

-   Null (Featureless) Model: Simple expectation \(E[Y]\) for RMSE.
-   Best Single Variable Model: \(max_{X_i \in X} E[Y|X_i=x_i]\)
-   Naive Bayes: naive lower bound
-   Current Performance: practical lower bound
-   Bayes Error Estimates: the upper bound of the data set (try estimating by resampling kNN)

see: 

-   [Setting Expectations](http://www.win-vector.com/blog/2012/04/setting-expectations-in-data-science-projects/) [Win-Vector blog]


<a id="orgbe482f7"></a>

# Feature Engineering and Model Selection

Understand the data. Use domain knowledge and visualization.

Understand how your data will interact with your algorithms. Be aware of:

-   Factor encodings
-   Outliers and robustness assumptions
-   Missing data
-   Statistical assumptions (especially, normality and homoskedasticity)
-   Sensitivity to scale
-   High correlation
-   Rank deficiency (linear dependence)
-   Noninformative features (regularization)
-   Feature interactions and nonlinearity
-   High dimensionality
-   Computational complexity
-   Convergence rates (some algorithms require a lot of data to make accurate estimates)
-   Sparsity

Consider representation learning methods:

-   the PCA family: linear, nonlinear, kernel, probabilistic, IDA, FA, categorical, MCA, HOMALS
-   Autoencoders (which is like nonlinear PCA)
-   Response encodings
-   Missing value imputation

Data Transforms:

-   log transforms
-   Box-Cox family

Feature Selection:

-   Filters
-   Wrappers
-   Embedded

When you are transforming the data it is important to ask: Is the transformation data-dependent? Does it depend on the features? Does it depend on the response? If so, it ought to be part of a validation procedure. This is important to avoid overfitting. Independent transformations can be applied at will, however.


<a id="orgf51ed2c"></a>

# Training and Tuning

Consider model aggregation methods: bagging, model averaging, ensembles, SuperLearning. You want a collection of models giving imperfectly correlated predictions. You may be able to reduce hyperparameter optimization and feature selection this way. (Put a sample of models in and let the superlearner select from them.)

If a particular statistic is of interest, consider Targeted Learning.


<a id="org5c8369b"></a>

# Model Evaluation

-   Residuals

-   Permutation Tests: Compare to the same model fit on a randomised response. Can help detect overfitting.

-   Benchmarking

Examining the residuals is very important This can help you to determine whether your model is well-specified. You want the residuals to look like "white noise". Look at QQ-plots or wormplots.

Compare a parametric model to some non-parametric equivalent. If the parametric model is well-specified, it should outperform the non-parametric model. This is because a parametric model should be able to "leverage its assumptions."

see: 

-   [Is Your Model Going to Work?](http://www.win-vector.com/blog/2015/09/isyourmodelgoingtowork/) [Win-Vector blog]


<a id="org97f16bd"></a>

# Model Interpretation


<a id="orgeb66f31"></a>

# Reporting and Deployment


<a id="orgc2b733a"></a>

# References

On process, see:

-   [Khun, M. *Applied Predictive Modeling*](http://appliedpredictivemodeling.com/) [book]
-   [Mount, J., Zumel, N. *Practical Data Science with R*](http://www.win-vector.com/blog/practical-data-science-with-r/) [book]
-   [DrWhy. *Model Development Process*](https://github.com/ModelOriented/DrWhy/blob/master/images/ModelDevelopmentProcess.pdf) [GitHub]

On data validation, see:

-   [de Jonge, E., & van der Loo, M. *Statistical Data Cleaning with Applications in R.*](https://www.wiley.com/en-us/Statistical+Data+Cleaning+with+Applications+in+R-p-9781118897157) [book] and the [\`validate\`](https://github.com/data-cleaning) R package [Github]

On experimental design, see:

-   [Atkinson, A. C., Donev, A. N., & Tobias, R. D. *Optimum experimental designs, with SAS.*](https://global.oup.com/academic/product/optimum-experimental-designs-with-sas-9780199296606?cc=us&lang=en&) [book]
-   [Santner, T., Williams, B., & Notz, W., *The design and analysis of computer experiments.*](https://www.springer.com/gp/book/9781441929921) [book]

On models generally, see:

-   [Shalizi, C. R. *Data Analysis from an Elementary Point of View.*](https://www.stat.cmu.edu/~cshalizi/ADAfaEPoV/) [free book]
-   [Hastie, T., Tibshirani, R., & Friedman, J., *Elements of Statistical Learning.*](https://web.stanford.edu/~hastie/ElemStatLearn/) [free book]
-   [Efron, B., & Hastie, T. *Computer Age Statistical Inference.*](http://web.stanford.edu/~hastie/CASI/) [free book]
-   [Murphy, K. P. *Machine learning: a probabilistic perspective.*](https://www.cs.ubc.ca/~murphyk/MLbook/) [book]
-   [Berk, R. *Statistical learning from a regression perspective.*](https://www.springer.com/gp/book/9780387775005) [book]
-   [Mohri, M., Rostamizadeh, A., & Talwalkar, A., *Foundations of machine learning.*](https://cs.nyu.edu/~mohri/mlbook/) [free book]

On deep learning, see:

-   [Goodfellow, I., Bengio, Y., & Courville, A. *Deep Learning.*](http://www.deeplearningbook.org/) [free book]

On time series, see:

-   [Hamilton, J. D., *Time Series Analysis.*](https://press.princeton.edu/books/hardcover/9780691042893/time-series-analysis) [book]
-   [Sanchez, J., *Hidden Markov Models for Time Series - An Introduction Using R.*](http://dx.doi.org/10.18637/jss.v043.b04) [book]

On feature engineering, see:

-   [Khun, M., Johnson, K. *Feature Engineering and Selection*](https://bookdown.org/max/FES/) [free book]
-   [Koch, I. *Analysis of Multivariate and High-Dimensional Data.*](https://www.cambridge.org/core/books/analysis-of-multivariate-and-highdimensional-data/2BF8DE949E18E3A68001976784087816) [book]
-   [Gifi, A., *Nonlinear Multivariate Analysis.*](https://www.wiley.com/en-us/Nonlinear+Multivariate+Analysis-p-9780471926207) [book] and an updated (but incomplete) version [de Leeuw, J., Mair, P., & Groenen, P., *Multivariate Analysis with Optimal Scaling.*](https://bookdown.org/jandeleeuw6/gifi/) [book] and the [\`gifi\`](https://cran.r-project.org/web/packages/Gifi/index.html) [CRAN] R package. PCA style optimal scaling.
-   [Harrell, F. E., *Regression modeling strategies.* Chapter 16](http://biostat.mc.vanderbilt.edu/wiki/Main/RmS) [book] and the [\`acepack\`](https://cran.r-project.org/web/packages/acepack/index.html) [CRAN] R package. Optimal nonparametric data transforms.

On validation and resampling, see:

-   [Raschka, S. *Evaluation, Model Selection, and Algorithm Selection in Machine Learning.*](https://arxiv.org/abs/1811.12808) [arXiv]
-   [Efron, B., & Tibshirani, R., *An introduction to the bootstrap.*](https://www.crcpress.com/An-Introduction-to-the-Bootstrap/Efron-Tibshirani/p/book/9780412042317) [book]
-   [Chernick, M. R., *Bootstrap methods: a guide for practitioners and researchers.*](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470192573) [book]
-   [Good, P. I., *Permutation, parametric and bootstrap tests of hypotheses.*](https://www.springer.com/gp/book/9781475723465) [book]
-   [Lahiri, S. N., *Resampling methods for dependent data.*](https://www.springer.com/gp/book/9780387009285) [book]

On model interpretation, see:

-   [Biecek, P. and Burzykowski, T., *Predictive Models: Explore, Explain, and Debug.*](https://pbiecek.github.io/PM_VEE/) [book] and [DrWhy](https://github.com/ModelOriented/DrWhy) [GitHub] R package

On statistics and mathematics, see:

-   [Jaynes, E. T., *Probability theory: the logic of science.*](https://www.cambridge.org/core/books/probability-theory/9CA08E224FF30123304E6D8935CF1A99) [book] A bit sprawling to serve as an introduction, though has much food for though on Bayesian probability.
-   [Casella, G., & Berger, R. L., *Statistical Inference.*](https://books.google.com/books/about/Statistical_Inference.html?id=xA7vAAAAMAAJ) [book]
-   [Deisenroth, M. P., Faisal, A. A., & Ong, C. S., *Mathematics for Machine Learning.*](https://mml-book.github.io/) [free book] Calculus, linear algebra, probability, optimization, with applications to common models. Quite good.
-   [Gallier, J., & Quaintance, J., *Algebra, Topology, Diﬀerential Calculus, and Optimization Theory For Computer Science and Machine Learning.*](https://www.cis.upenn.edu/~jean/gbooks/home.html) More advanced and more comprehensive. The first author has a number of other relevant textbooks on his website. [free book]
-   [Pollard, D., *A user's guide to measure theoretic probability.*](https://www.cambridge.org/core/books/users-guide-to-measure-theoretic-probability/A257FE6572A9142FE3B811FFF3FD0171) A good introduction to measure theory, if you're into that sort of thing. [book]
-   [Schervish, M. J., *Theory of Statistics.*](https://www.springer.com/gp/book/9780387945460) Like Casella with measure theory. [book]

