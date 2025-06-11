# Machine Learning and AI Workbook

This is a working document meant to take notes as I work through learning:

- Machine Learning
- Mathematical Foundations of Machine Learning
- Artificial Intelligence
- Neural Networks
- Large Language Models
- MLOps (Machine Learning Operations)

## Section 1 - Linear Regressions (Introduction)

**Linear Regression: Uncovering Relationships Between Variables**

Linear regression is a fundamental statistical method used to model the relationship between two or more variables by fitting a linear equation to observed data. Think of it as drawing the "best-fit" straight line through a scatter plot of your data points.

**The Core Idea: Predicting an Outcome from Predictors**

At its heart, linear regression aims to predict a dependent variable (also called the "response" or "outcome") based on the values of one or more independent variables (also called "predictors" or "features").

### Simple Linear Regression

# Linear Regression: Uncovering Relationships Between Variables

Linear regression is a fundamental statistical method used to model the relationship between two or more variables by fitting a linear equation to observed data. Think of it as drawing the "best-fit" straight line through a scatter plot of your data points.

## The Core Idea: Predicting an Outcome from Predictors

At its heart, linear regression aims to predict a **dependent variable** (also called the "response" or "outcome") based on the values of one or more **independent variables** (also called "predictors" or "features").

**Example:**
* **Dependent Variable:** House price
* **Independent Variable:** Size of the house (square footage)

Linear regression would try to find a linear relationship that allows you to predict a house's price given its size.

## The Math Behind It (Simple Linear Regression)

For simplicity, let's start with **Simple Linear Regression**, where we have one independent variable ($X$) and one dependent variable ($Y$). The equation that describes this linear relationship is:

$$ Y = \beta_0 + \beta_1 X + \epsilon $$

Let's break down each component:

* $Y$: This is the **dependent variable** you are trying to predict.
* $X$: This is the **independent variable** you are using to make the prediction.
* $\beta_0$ (Beta-naught): This is the **Y-intercept**. It's the predicted value of $Y$ when $X$ is 0. In our house price example, it might represent a base price of a house, even if it had "0" square footage (though this interpretation needs careful consideration for real-world scenarios where $X=0$ might not make sense).
* $\beta_1$ (Beta-one): This is the **slope** of the line. It tells you how much $Y$ is expected to change for every one-unit increase in $X$. For house prices, if $\beta_1$ is $100, it means that for every additional square foot, the house price is expected to increase by $100.
* $\epsilon$ (Epsilon): This is the **error term** or residual. It represents the difference between the actual observed value of $Y$ and the value predicted by our linear model. No model is perfect, so there's always some unexplained variation or noise.

#### Mathematics of Basic Linear Regression
## The Math Behind It (Simple Linear Regression)

For simplicity, let's start with **Simple Linear Regression**, where we have one independent variable ($X$) and one dependent variable ($Y$). The equation that describes this linear relationship is:

$$Y = \beta_0 + \beta_1 X + \epsilon$$

Let's break down each component:

* $Y$: This is the **dependent variable** you are trying to predict.
* $X$: This is the **independent variable** you are using to make the prediction.
* $\beta_0$ (Beta-naught): This is the **Y-intercept**. It's the predicted value of $Y$ when $X$ is 0.
* $\beta_1$ (Beta-one): This is the **slope** of the line. It tells you how much $Y$ is expected to change for every one-unit increase in $X$.
* $\epsilon$ (Epsilon): This is the **error term** or residual. It represents the difference between the actual observed value of $Y$ and the value predicted by our linear model.

### Step 1: Define "Best Fit" (The Cost Function)

To find the "best-fit" line, we need a way to quantify how good a fit a particular line is. Linear Regression uses the **Ordinary Least Squares (OLS)** method, which minimizes the **Sum of Squared Errors (SSE)**.

For each data point $(x_i, y_i)$, the error (or residual) $e_i$ is the vertical distance between the actual observed value $y_i$ and the value $\hat{y}_i$ predicted by our line:

$$e_i = y_i - \hat{y}_i = y_i - (\beta_0 + \beta_1 x_i)$$

The **Sum of Squared Errors (SSE)** is the sum of these squared residuals for all $n$ data points:

$$SSE = \sum_{i=1}^{n} e_i^2 = \sum_{i=1}^{n} (y_i - (\beta_0 + \beta_1 x_i))^2$$

Our goal is to find the values of $\beta_0$ and $\beta_1$ that make this $SSE$ as small as possible.

### Step 2: Calculate the Slope ($\beta_1$) and Intercept ($\beta_0$)

Fortunately, for simple linear regression, there are closed-form solutions (direct formulas) derived using calculus (minimizing the SSE function) that give us the exact values for $\beta_0$ and $\beta_1$.

1.  **Slope ($\beta_1$):**
    The formula for the optimal slope $\beta_1$ is:

    $$\beta_1 = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n} (x_i - \bar{x})^2}$$

    Where:
    * $n$ is the total number of data points.
    * $x_i$ and $y_i$ are the values of the independent and dependent variables for the $i$-th data point.
    * $\bar{x}$ is the mean (average) of all $X$ values.
    * $\bar{y}$ is the mean (average) of all $Y$ values.

    **Intuitive Breakdown:**
    * **Numerator:** $\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})$ measures how $X$ and $Y$ *covary* (change together) around their respective means. If large $X$ values tend to go with large $Y$ values, and small $X$ with small $Y$, this term will be positive.
    * **Denominator:** $\sum_{i=1}^{n} (x_i - \bar{x})^2$ measures the *variance* or spread of the $X$ values.

2.  **Intercept ($\beta_0$):**
    Once the slope $\beta_1$ is calculated, the intercept $\beta_0$ can be found using the fact that the regression line *always passes through the mean of the data points* ($\bar{x}, \bar{y}$).

    $$\beta_0 = \bar{y} - \beta_1 \bar{x}$$

    These two formulas provide the unique line that minimizes the sum of squared vertical distances from all data points to the line.


**Discussion**
---

#### Why Dividing the Numerator by the Denominator Gives Us the "Best" Slope

Now, let's put it all together. Recall the formula for $\beta_1$:

$$\beta_1 = \frac{\sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n} (x_i - \bar{x})^2}$$

We can conceptually express this as:

$$
\beta_1 = \frac{\text{Measure of how X and Y vary together (Covariance-like)}}{\text{Measure of how X varies (Variance-like)}}
$$

* **It's still "Rise over Run," but averaged and weighted for many points.**
    * The **Numerator** is a weighted sum of "rises" – how much $Y$ changes, proportional to how $X$ changes, relative to their centers. It indicates the **direction and magnitude of the co-movement** between $X$ and $Y$.
    * The **Denominator** is a weighted sum of "runs" – the total spread of the $X$ values. It normalizes the "rise" by the extent of the "run," ensuring the slope is scaled correctly based on the variability of $X$.

* **How it finds the "best" line (via OLS derivation):**
    The formula for $\beta_1$ isn't just an arbitrary definition of "rise over run." It's derived directly from minimizing the **Sum of Squared Errors (SSE)**.

    Imagine the SSE as a 3D bowl shape where the axes are $\beta_0$, $\beta_1$, and the SSE value (the error) is the height. Our goal is to find the lowest point in that bowl.

    By setting the partial derivatives of the SSE with respect to $\beta_0$ and $\beta_1$ to zero, you find the exact "bottom" of that bowl – the unique combination of $\beta_0$ and $\beta_1$ that results in the smallest possible SSE. The formulas for $\beta_1$ and $\beta_0$ are the analytical solutions to those equations.

In essence, this formula for $\beta_1$ isn't just a heuristic; it's the **mathematically proven value** that defines the slope of the line that is closest, on average (in terms of squared vertical distance), to all your data points. It balances the upward/downward trend (numerator) with the overall spread of your independent variable (denominator) to give you the most representative linear relationship.

### K-Nearest Neighbors - kNN

kNN is a non-parametric learning algorithm, meaning that there is no assumptions about the underlying data distribution. The k-Nearest Neighbor Algorithm can be described more formally. Given a dataset $D = (X_1, y_1), \dots, (X_N, y_N)$, for every new $X$:

1.  Find the k-number of observations in $D$ most similar to $X$:
    $$ (X^{(n_1)}, y^{(n_1)}), \dots, (X^{(n_k)}, y^{(n_k)}) $$
    These are called the k-nearest neighbors of $x$

2.  Average the output of the k-nearest neighbors of $x$
    $$ \hat{y} = \frac{1}{K} \sum_{k=1}^{K} y^{(n_k)} $$