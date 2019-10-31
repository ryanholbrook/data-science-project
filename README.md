
# Data Science Project Overview


# Table of Contents

1.  [Determine Objectives](#org77f8fa9)
2.  [Collect Data](#org517c0f3)
    1.  [Experimental Design](#orge516021)
3.  [Specify Data](#orgcde0099)
    1.  [Determine Types and Representation](#org3932fa5)
    2.  [Determine Roles](#org10fb7fb)
4.  [Correct Data](#org38ce769)
    1.  [Determine Validation Rules](#orgb00d064)
    2.  [String Correction](#org4f01832)
    3.  [Numeric Correction](#org69ac40d)
    4.  [Missing Correction](#orgc68dd25)
5.  [Model Validation Scheme](#org80074e8)
6.  [Prior Expectations](#org74c3745)
7.  [Feature Engineering and Model Selection](#orgdde3513)
8.  [Training and Tuning](#orgb545f0f)
9.  [Model Evaluation](#org61b63c9)
10. [Model Deployment and Reporting](#orgcb8e20d)


<a id="org77f8fa9"></a>

# Determine Objectives

Determine Constraints. Do you want predictions? Does the model need to be interpretable? What resources do you have?

Define success. How do you know you're done?

Understand utilities. What are the costs of erroneous predictions? What are the benefits of correct predictions?


<a id="org517c0f3"></a>

# Collect Data

Collect the data in raw form, if not provided.


<a id="orge516021"></a>

## Experimental Design


<a id="orgcde0099"></a>

# Specify Data

Determine what properties the data should have.


<a id="org3932fa5"></a>

## Determine Types and Representation

See [Statistical Data Type](https://en.wikipedia.org/wiki/Statistical_data_type) [Wikipedia]

-   Binary: Integer or Logical
-   Nominal: Factor
-   Ordinal: Ordered Factor
-   Continuous: Float
-   Linear Temporal: Date
-   Cyclic Temporal: Factor
-   Text: String

Data Frame
Time Series
Matrix
Relational Database
Non-relational Database
Graph


<a id="org10fb7fb"></a>

## Determine Roles

Feature
Response
Identity
Information


<a id="org38ce769"></a>

# Correct Data

Decide on how to correct erroneous data. Understanding why the data is erroneous is important. Visualization tools can help.

Many errors can be corrected through an automatic application of rules. For others, error localization can be used to remove any uncorrectable fields.

Correct observed data before imputing missing data.

see: [de Jonge, E., & van der Loo, M. *Statistical Data Cleaning with Applications in R.*](https://www.wiley.com/en-us/Statistical+Data+Cleaning+with+Applications+in+R-p-9781118897157) and [`validate`](https://github.com/data-cleaning) [Github]


<a id="orgb00d064"></a>

## Determine Validation Rules

Specify what properties the data must have to be "clean". Domain knowledge is essential here.


<a id="org4f01832"></a>

## String Correction


<a id="org69ac40d"></a>

## Numeric Correction


<a id="orgc68dd25"></a>

## Missing Correction


<a id="org80074e8"></a>

# Model Validation Scheme

Decide on validation procedures (for feature engineering, performance, tuning, benchmarking) and make data splits.

see: [Raschka, S. *Evaluation, Model Selection, and Algorithm Selection in Machine Learning.*](https://arxiv.org/abs/1811.12808) [arXiv]


<a id="org74c3745"></a>

# Prior Expectations

Look at simple baselines.

-   Simple expectation \(E[Y]\): featureless lower bound
-   Naive Bayes: naive lower bound
-   Current Performance: practical lower bound
-   Bayes Error Estimates: the upper bound of the data set (try estimating by resampling kNN)

see: [Setting Expectations](http://www.win-vector.com/blog/2012/04/setting-expectations-in-data-science-projects/) (Win-Vector blog)


<a id="orgdde3513"></a>

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


<a id="orgb545f0f"></a>

# Training and Tuning

Consider model aggregation methods: bagging, model averaging, ensembles, SuperLearning. You want a collection of models giving imperfectly correlated predictions. You may be able to reduce hyperparameter optimization and feature selection this way. (Put a sample of models in and let the superlearner select from them.)

If a particular statistic is of interest, consider Targeted Learning.


<a id="org61b63c9"></a>

# Model Evaluation

Compare models through benchmarking. 

Examine the residuals. This can help you to determine whether your model is well-specified. You want the residuals to look like "white noise". Look at QQ-plots or wormplots.

Compare a parametric model to some non-parametric equivalent. If the parametric model is well-specified, it should outperform the non-parametric model. This is because a parametric model should be able to "leverage its assumptions."

see: [Shalizi, C. R. *Data Analysis from an Elementary Point of View.*](https://www.stat.cmu.edu/~cshalizi/ADAfaEPoV/) [book]


<a id="orgcb8e20d"></a>

# Model Deployment and Reporting



