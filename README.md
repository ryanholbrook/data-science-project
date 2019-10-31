
# Data Science Project Overview

# Table of Contents

1.  [Determine Objectives](#org20f1889)
2.  [Collect Data](#orgc863def)
    1.  [Experimental Design](#org14cf39a)
3.  [Specify Data](#orgcdc50f7)
    1.  [Determine Types and Representation](#org9e3eb88)
    2.  [Determine Roles](#org020628b)
4.  [Correct Data](#orga580069)
    1.  [Determine Validation Rules](#orge957fcc)
    2.  [String Correction](#org64ed03a)
    3.  [Numeric Correction](#orgd3ccf71)
    4.  [Missing Correction](#orgdfa030a)
5.  [Model Validation Scheme](#orgf6f0005)
6.  [Prior Expectations](#orgf074cf4)
7.  [Feature Engineering and Model Selection](#orgd9f0672)
8.  [Training and Tuning](#orgc715cad)
9.  [Model Evaluation](#org5ffe0f2)
10. [Model Deployment and Reporting](#orgde763c9)


<a id="org20f1889"></a>

# Determine Objectives

Determine Constraints. Do you want predictions? Does the model need to be interpretable? What resources do you have?

Define success. How do you know you're done?

Understand utilities. What are the costs of erroneous predictions? What are the benefits of correct predictions?


<a id="orgc863def"></a>

# Collect Data

Collect the data in raw form, if not provided.


<a id="org14cf39a"></a>

## Experimental Design


<a id="orgcdc50f7"></a>

# Specify Data

Determine what properties the data should have.


<a id="org9e3eb88"></a>

## Determine Types and Representation

See [Statistical Data Type](https://en.wikipedia.org/wiki/Statistical_data_type) [Wikipedia]

Binary - Integer or Logical
Nominal - Factor
Ordinal - Ordered Factor
Continuous - Float
Linear Temporal - Date
Cyclic Temporal - Factor
Text - String

Data Frame
Time Series
Matrix
Relational Database
Non-relational Database
Graph


<a id="org020628b"></a>

## Determine Roles

Feature
Response
Identity
Information


<a id="orga580069"></a>

# Correct Data

Decide on how to correct erroneous data. Understanding why the data is erroneous is important. Visualization tools can help.

Many errors can be corrected through an automatic application of rules. For others, error localization can be used to remove any uncorrectable fields.

Correct observed data before imputing missing data.

see: [de Jonge, E., & van der Loo, M. *Statistical Data Cleaning with Applications in R.*](https://www.wiley.com/en-us/Statistical+Data+Cleaning+with+Applications+in+R-p-9781118897157) and [`validate`](https://github.com/data-cleaning) [Github]


<a id="orge957fcc"></a>

## Determine Validation Rules

Specify what properties the data must have to be "clean". Domain knowledge is essential here.


<a id="org64ed03a"></a>

## String Correction


<a id="orgd3ccf71"></a>

## Numeric Correction


<a id="orgdfa030a"></a>

## Missing Correction


<a id="orgf6f0005"></a>

# Model Validation Scheme

Decide on validation procedures (for feature engineering, performance, tuning, benchmarking) and make data splits.

see: [Raschka, S. *Evaluation, Model Selection, and Algorithm Selection in Machine Learning.*](https://arxiv.org/abs/1811.12808) [arXiv]


<a id="orgf074cf4"></a>

# Prior Expectations

Look at simple baselines.

-   Simple expectation \(E[Y]\): featureless lower bound
-   Naive Bayes: naive lower bound
-   Current Performance: practical lower bound
-   Bayes Error Estimates: the upper bound of the data set (try estimating by resampling kNN)

see: [Setting Expectations](http://www.win-vector.com/blog/2012/04/setting-expectations-in-data-science-projects/) (Win-Vector blog)


<a id="orgd9f0672"></a>

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

-   filters
-   wrappers
-   embedded

When you are transforming the data it is important to ask: Is the transformation data-dependent? Does it depend on the features? Does it depend on the response? If so, it ought to be part of a validation procedure. Independent transformations can be applied at will, however. This is important to avoid overfitting.

see: [Khun, M., Johnson, K. *Feature Engineering and Selection*](https://bookdown.org/max/FES/) [book]


<a id="orgc715cad"></a>

# Training and Tuning

Consider model aggregation methods: bagging, model averaging, ensembles, SuperLearning. You want a collection of models giving imperfectly correlated predictions. You may be able to reduce hyperparameter optimization and feature selection this way. (Put a sample of models in and let the superlearner select from them.)

If a particular statistic is of interest, consider Targeted Learning.


<a id="org5ffe0f2"></a>

# Model Evaluation

Compare models through benchmarking. 

Examine the residuals. This can help you to determine whether your model is well-specified. You want the residuals to look like "white noise". Look at QQ-plots or wormplots.

Compare a parametric model to some non-parametric equivalent. If the parametric model is well-specified, it should outperform the non-parametric model. This is because a parametric model should be able to "leverage its assumptions."

see: [Shalizi, C. R. *Data Analysis from an Elementary Point of View.*](https://www.stat.cmu.edu/~cshalizi/ADAfaEPoV/) [book]


<a id="orgde763c9"></a>

# Model Deployment and Reporting

