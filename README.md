
# Table of Contents

1.  [Objectives](#org7fcfba1)
2.  [Data Collection](#org04e3d52)
    1.  [Experimental Design](#org5de370d)
3.  [Data Specification](#org3e8354f)
    1.  [Determine Statistical Type](#org64ac458)
    2.  [Determine Roles](#org8566a6c)
    3.  [Determine Validation Rules](#org3901367)
4.  [Data Correction](#org896f512)
    1.  [String Correction](#orge1e5960)
    2.  [Numeric Correction](#org9e7b8bc)
    3.  [Missing Correction](#org321df15)
5.  [Determine Model Validation Scheme](#orga5fda1b)
6.  [Establish Baseline Performance and Evaluation Metrics](#orgf7e4e4b)
7.  [Feature Engineering and Model Selection](#org18a192e)
8.  [Training and Tuning](#orgc19f69d)
9.  [Model Evaluation](#orgbd05d90)
10. [Model Interpretation](#org3ee73ed)
11. [Model Deployment and Reporting](#orgf246770)
12. [References](#orgf29ac59)



<a id="org7fcfba1"></a>

# Objectives

Determine Constraints. Do you want predictions? Does the model need to be interpretable? What resources do you have?

Define success. How do you know you're done?

Understand utilities. What are the costs of erroneous predictions? What are the benefits of correct predictions?


<a id="org04e3d52"></a>

# Data Collection

Collect the data in raw form, if not provided.


<a id="org5de370d"></a>

## Experimental Design

Statistically optimal ways of collecting data. The mantra is: *To get the most from your experiments, reduce the variance.* (Good 2005)

Consider active learning if you need to label data.


<a id="org3e8354f"></a>

# Data Specification

Determine what properties the data should have.


<a id="org64ac458"></a>

## Determine Statistical Type

-   Binary: Integer or Logical
-   Nominal: Factor
-   Ordinal: Ordered Factor
-   Continuous: Float
-   Linear Temporal: Date
-   Cyclic Temporal: Factor
-   Text: String

See [Statistical Data Type](https://en.wikipedia.org/wiki/Statistical_data_type) [Wikipedia]


<a id="org8566a6c"></a>

## Determine Roles

-   Feature
-   Response
-   Identity
-   Information


<a id="org3901367"></a>

## Determine Validation Rules

Specify what properties the data must have to be "clean". Domain knowledge is essential here.


<a id="org896f512"></a>

# Data Correction

Decide on how to correct erroneous data. Understanding why the data is erroneous is important. Visualization tools can help.

Many errors can be corrected through an automatic application of rules. For others, error localization can be used to remove any uncorrectable fields.

Correct observed data before imputing missing data.


<a id="orge1e5960"></a>

## String Correction


<a id="org9e7b8bc"></a>

## Numeric Correction


<a id="org321df15"></a>

## Missing Correction


<a id="orga5fda1b"></a>

# Determine Model Validation Scheme

Decide on validation procedures (for feature engineering, performance, tuning, benchmarking) and make data splits.


<a id="orgf7e4e4b"></a>

# Establish Baseline Performance and Evaluation Metrics

-   Null (Featureless) Model: Simple expectation \(E[Y]\) for RMSE.
-   Best Single Variable Model: \(max_{X_i \in X} E[Y|X_i=x_i]\)
-   Naive Bayes: naive lower bound
-   Current Performance: practical lower bound
-   Bayes Error Estimates: the upper bound of the data set (try estimating by resampling kNN)

see: 

-   [Setting Expectations](http://www.win-vector.com/blog/2012/04/setting-expectations-in-data-science-projects/) [Win-Vector blog]


<a id="org18a192e"></a>

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


<a id="orgc19f69d"></a>

# Training and Tuning

Consider model aggregation methods: bagging, model averaging, ensembles, SuperLearning. You want a collection of models giving imperfectly correlated predictions. You may be able to reduce hyperparameter optimization and feature selection this way. (Put a sample of models in and let the superlearner select from them.)

If a particular statistic is of interest, consider Targeted Learning.


<a id="orgbd05d90"></a>

# Model Evaluation

-   Residuals

-   Permutation Tests: Compare to the same model fit on a randomised response. Can help detect overfitting.

-   Benchmarking

Examining the residuals is very important This can help you to determine whether your model is well-specified. You want the residuals to look like "white noise". Look at QQ-plots or wormplots.

Compare a parametric model to some non-parametric equivalent. If the parametric model is well-specified, it should outperform the non-parametric model. This is because a parametric model should be able to "leverage its assumptions."

see: 

-   [Is Your Model Going to Work?](http://www.win-vector.com/blog/2015/09/isyourmodelgoingtowork/) [Win-Vector blog]


<a id="org3ee73ed"></a>

# Model Interpretation


<a id="orgf246770"></a>

# Model Deployment and Reporting


<a id="orgf29ac59"></a>

# References

On process, see:

-   [Khun, M. *Applied Predictive Modeling*](http://appliedpredictivemodeling.com/) [book]
-   [Mount, J., Zumel, N. *Practical Data Science with R*](http://www.win-vector.com/blog/practical-data-science-with-r/) [book]
-   [DrWhy. *Model Development Process*](https://github.com/ModelOriented/DrWhy/blob/master/images/ModelDevelopmentProcess.pdf) [GitHub]

On data validation, see:

-   [de Jonge, E., & van der Loo, M. *Statistical Data Cleaning with Applications in R.*](https://www.wiley.com/en-us/Statistical+Data+Cleaning+with+Applications+in+R-p-9781118897157) [book] and the [\`validate\`](https://github.com/data-cleaning) R package [Github]

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
-   [Harrell, F. E., Regression modeling strategies](http://biostat.mc.vanderbilt.edu/wiki/Main/RmS) [book] and the [\`acepack\`](https://cran.r-project.org/web/packages/acepack/index.html) [CRAN] R package. Optimal scaling for regression models.

On validation and resampling, see:

-   [Raschka, S. *Evaluation, Model Selection, and Algorithm Selection in Machine Learning.*](https://arxiv.org/abs/1811.12808) [arXiv]
-   [Efron, B., & Tibshirani, R., *An introduction to the bootstrap.*](https://www.crcpress.com/An-Introduction-to-the-Bootstrap/Efron-Tibshirani/p/book/9780412042317) [book]
-   [Chernick, M. R., *Bootstrap methods: a guide for practitioners and researchers.*](https://onlinelibrary.wiley.com/doi/book/10.1002/9780470192573) [book]
-   [Good, P. I., *Permutation, parametric and bootstrap tests of hypotheses.*](https://www.springer.com/gp/book/9781475723465) [book]
-   [Lahiri, S. N., *Resampling methods for dependent data.*](https://www.springer.com/gp/book/9780387009285) [book]

On model interpretation, see:

-   [Biecek, P. and Burzykowski, T., *Predictive Models: Explore, Explain, and Debug.*](https://pbiecek.github.io/PM_VEE/) [book] and [DrWhy](https://github.com/ModelOriented/DrWhy) [GitHub] R package

On statistics and mathematics, see:

-   [Casella, G., & Berger, R. L., *Statistical Inference.*](https://books.google.com/books/about/Statistical_Inference.html?id=xA7vAAAAMAAJ) [book]
-   [Gallier, J., & Quaintance, J., *Algebra, Topology, Diﬀerential Calculus, and Optimization Theory For Computer Science and Machine Learning.*](https://www.cis.upenn.edu/~jean/gbooks/home.html) [free book]
-   [Pollard, D., *A user's guide to measure theoretic probability.*](https://www.cambridge.org/core/books/users-guide-to-measure-theoretic-probability/A257FE6572A9142FE3B811FFF3FD0171) [book]

