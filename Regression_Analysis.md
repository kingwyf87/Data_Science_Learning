# Regression Analysis
There are multiple benefits of using regression analysis. They are as follows:

1. It indicates the significant relationships between dependent variable and independent variable.
2. It indicates the strength of impact of multiple independent variables on a dependent variable.

## 1. Linear Regression
 In this technique, the dependent variable is continuous, independent variable(s) can be continuous or discrete, and nature of regression line is linear.

 Linear Regression establishes a relationship between dependent variable ($Y$) and one or more independent variables ($X$) using a best fit straight line (also known as regression line).

 It is represented by an equation $Y=a+b*X + e$, where $a$ is intercept, $b$ is slope of the line and $e$ is error term. This equation can be used to predict the value of target variable based on given predictor variable(s).

Important Points:

1. There must be **linear relationship** between independent and dependent variables
2. Multiple regression suffers from **multicollinearity, autocorrelation, heteroskedasticity**.
3. Linear Regression is very sensitive to **Outliers**. It can terribly affect the regression line and eventually the forecasted values.
4. Multicollinearity can increase the variance of the coefficient estimates and make the estimates very sensitive to minor changes in the model. The result is that the coefficient estimates are unstable
5. In case of multiple independent variables, we can go with **forward selection, backward elimination and step wise approach** for selection of most significant independent variables.

## 2. Logistic Regression
Logistic regression is used to find the probability of event=Success and event=Failure. We should use logistic regression when the dependent variable is binary (0/ 1, True/ False, Yes/ No) in nature.

In the equation, the parameters are chosen to maximize the likelihood of observing the sample values rather than minimizing the sum of squared errors (like in ordinary regression).

Important Points:

1. It is widely used for **classification problems**
2. Logistic regression doesn’t require linear relationship between dependent and independent variables.  It can handle various types of relationships because it applies a non-linear log transformation to the predicted odds ratio
3. To avoid over fitting and under fitting, we should include all significant variables. A good approach to ensure this practice is to use a step wise method to estimate the logistic regression
4. It requires **large sample sizes** because maximum likelihood estimates are less powerful at low sample sizes than ordinary least square
5. The independent variables should not be correlated with each other i.e. **no multi collinearity**.  However, we have the options to include interaction effects of categorical variables in the analysis and in the model.
6. If the values of dependent variable is ordinal, then it is called as **Ordinal logistic regression**
If dependent variable is multi class then it is known as **Multinomial Logistic regression**.

## 3. Polynomial Regression
A regression equation is a polynomial regression equation if the power of independent variable is more than 1. The equation below represents a polynomial equation: $y=a+b*x^2$

Important Points:

1. While there might be a temptation to fit a higher degree polynomial to get lower error, this can result in over-fitting. Always plot the relationships to see the fit and focus on making sure that the curve fits the nature of the problem.
2. Especially look out for curve towards the ends and see whether those shapes and trends make sense. Higher polynomials can end up producing wierd results on extrapolation.

## 4. Stepwise Regression
This form of regression is used when we deal with multiple independent variables. In this technique, the selection of independent variables is done with the help of an automatic process, which involves no human intervention.

This feat is achieved by observing statistical values like R-square, t-stats and AIC metric to discern significant variables. Stepwise regression basically fits the regression model by adding/dropping co-variates one at a time based on a specified criterion. Some of the most commonly used Stepwise regression methods are listed below:

1. Standard stepwise regression does two things. It adds and removes predictors as needed for each step.
2. Forward selection starts with most significant predictor in the model and adds variable for each step.
3. Backward elimination starts with all predictors in the model and removes the least significant variable for each step.

## 5. Ridge Regression
Ridge Regression is a technique used when the data suffers from multicollinearity ( independent variables are highly correlated). In multicollinearity, even though the least squares estimates (OLS) are unbiased, their variances are large which deviates the observed value far from the true value. By adding a degree of bias to the regression estimates, ridge regression reduces the standard errors.

Ridge regression solves the multicollinearity problem through shrinkage parameter $\lambda$ (lambda).

\[||y-X\beta||+\lambda||\beta||_2^2\]

In this equation, we have two components. First one is least square term and other one is lambda of the summation of $β^2$ where β is the coefficient. This is added to least square term in order to shrink the parameter to have a very low variance.

Important Points:

1. The assumptions of this regression is same as least squared regression except normality is not to be assumed

2. It shrinks the value of coefficients but doesn't reaches zero, which suggests no feature selection feature
This is a regularization method and uses L2 regularization.

## 6. Lasso Regression

Similar to Ridge Regression, Lasso (Least Absolute Shrinkage and Selection Operator) also penalizes the absolute size of the regression coefficients. In addition, it is capable of reducing the variability and improving the accuracy of linear regression models.

\[||y-X\beta||+\lambda||\beta||_1\]

Lasso regression differs from ridge regression in a way that it uses absolute values in the penalty function, instead of squares. This leads to penalizing (or equivalently constraining the sum of the absolute values of the estimates) values which causes some of the parameter estimates to turn out exactly zero. Larger the penalty applied, further the estimates get shrunk towards absolute zero. This results to variable selection out of given $n$ variables.

Important Points:

1. The assumptions of this regression is same as least squared regression except normality is not to be assumed
2. It shrinks coefficients to zero (exactly zero), which certainly helps in feature selection
3. This is a regularization method and uses L1 regularization
If group of predictors are highly correlated, lasso picks only one of them and shrinks the others to zero

## 7. ElasticNet Regression
ElasticNet is hybrid of Lasso and Ridge Regression techniques. It is trained with L1 and L2 prior as regularizer. Elastic-net is useful when there are multiple features which are correlated. Lasso is likely to pick one of these at random, while elastic-net is likely to pick both.

\[||y-X\beta||+\lambda_1||\beta||_2^2 + \lambda_2||\beta||_1\]
A practical advantage of trading-off between Lasso and Ridge is that, it allows Elastic-Net to inherit some of Ridge’s stability under rotation.

Important Points:
1. It encourages group effect in case of highly correlated variables
2. There are no limitations on the number of selected variables
It can suffer with double shrinkage

Beyond these 7 most commonly used regression techniques, there are other models like Bayesian, Ecological and Robust regression.

## How to select the right regression model?

Within multiple types of regression models, it is important to choose the best suited technique based on type of independent and dependent variables, dimensionality in the data and other essential characteristics of the data. Below are the key factors that you should practice to select the right regression model:

1. Data exploration is an inevitable part of building predictive model. It should be you first step before selecting the right model like identify the relationship and impact of variables
2. To compare the goodness of fit for different models, we can analyse different metrics like statistical significance of parameters, R-square, Adjusted r-square, AIC, BIC and error term. Another one is the Mallow’s Cp criterion. This essentially checks for possible bias in your model, by comparing the model with all possible submodels (or a careful selection of them).
3. Cross-validation is the best way to evaluate models used for prediction. Here you divide your data set into two group (train and validate). A simple mean squared difference between the observed and predicted values give you a measure for the prediction accuracy.
4. If your data set has multiple confounding variables, you should not choose automatic model selection method because you do not want to put these in a model at the same time.
5. It’ll also depend on your objective. It can occur that a less powerful model is easy to implement as compared to a highly statistically significant model.
6. Regression regularization methods(Lasso, Ridge and ElasticNet) works well in case of high dimensionality and multicollinearity among the variables in the data set.
