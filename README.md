
<!-- README.md is generated from README.Rmd. Please edit that file -->

# linregasm

# Package for testing linear and multiple linear regression assumptions

This package is built to contain functions to be able to quickly and
easily test the linearity assumptions before preforming linear
regression or multiple linear regression for a specified dataset.

The package contains 3 functions one for checking multicolliniarity, one
for checking constant variance and one for checking normality in the
residuals. The three assumptions should be satisfied to ensure the
effectiveness of a linear regression model for a particular dataset and
are described as follows:

-   **No Multicollinearity**: individual predictors within a model
    should not be linearly correlated to avoid unstable linear
    estimators
-   **Constant Variance of Residuals (homoscedasticity)**: Since data
    should be individually and identically distributed, the residuals
    should be independent of fitted values
-   **Normality of residuals**: Since the conditional expectation of the
    predicted value should be normal, the error terms of the resulting
    model should also be normally distributed

Function 1: Multicolliniarity.

-   Takes a R dataframe and a VIF threshold and checks if any of the
    calculated vif values exceed the given threshold. If so, the
    function will advise the user that this assumtion is violated, and
    vice versa.

-   Returns the Calculated VIF values and a statement telling the user
    whether or not the assumpton is violated.

Function 2: Constant Variance.

-   Takes a R dataframe for the predictors, a R dataframe for the
    response and some sort of variability threshold and checks if the
    variabiliy of the residuals is contant by comparing it to the given
    threshold. If the threshold is exceeded the function will advise the
    user that this assumtion is violated, and vice versa.

-   Returns a plot of the fitted values vs residuals, the calculated
    variability value and a statement telling the user whether or not
    the assumpton is violated.

Function 3: Normality.

-   Takes a R dataframe for the predictors, a R dataframe for the
    response and performs a shapiro wilk test for normality. If the
    P-value of the test does not exceed the threshold, the function will
    advise the user that this assumtion is violated, and vice versa.

-   Returns the Calculated P-value and a statement telling the user
    whether or not the assumpton is violated.

## Installation

You can install the most revent version of linregasm from github using
the following code:

``` r
library(devtools)
install_github("UBC-MDS/linregasm")
```

You can install the released version of linregasm from
[CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("linregasm")
```

## Usage

To use linregasm to check linear regression assumptions in your own
projects, see the following usage example.

**Test for Normality** To test for normality, use the `normality()`
function and pass in your data and linear regression formula as follows:

    norm_results <- normality(data, formula)

**Test for Homoscedasticity** To test for homoscedasticity, use the
`homoscedasticity()` function as follows:

    hsc_results <- linregasm::homoscedasticity(iris_df, formula)

**Test for Multicollinearity** To test for homoscedasticity, use the
`multicollinearity()` function as follows:

    mult_results <- linregasm::multicollinearity(iris_df, formula)

## Ecosystem

As of January 2022, there are functions and packages which contain tools
for linear regression evaluation such as `plot()` in base R, or
`autoplot()` in `ggfortify`, which generate evaluation plots.
Additionally, there are many linear regression reporting tools contained
in packages such as `broom`, which tidies and reports linear regression
statistics. The linregasm package seeks to build upon existing R
packages, and to incorporate additional statistical tests that were not
previously present. This package aggregates the functions offered by
base R, broom, and more, seeking to build upon them for the purpose of
evaluating linear regression models. This is intended to make it more
accessible for users to access the functionality of the previously
mentioned packages, as well as improve the clarity of results.

## Contributing

Authors: Yair Guterman, Hatef Rahmani, Song Bo Andy Yang  
Interested in contributing? Check out the contributing guidelines.
Please note that this project is released with a Code of Conduct. By
contributing to this project, you agree to abide by its terms.

## License

`linregasm` was created by Yair Guterman, Hatef Rahmani, Song Bo Andy
Yang . It is licensed under the terms of the MIT license.
