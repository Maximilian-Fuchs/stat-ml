# Book: Introduction to Statistical Learning
[amazon link](https://www.amazon.de/Introduction-Statistical-Learning-Applications-Statistics/dp/1461471370)

---
### Notation
Datasets are denoted as $\textbf{X} = \begin{pmatrix}
x_{11} & x_{12} & \cdots & x_{1p}\\
x_{21} & x_{22} & \cdots & x_{2p}\\
\vdots & \vdots & \ddots & \vdots\\
x_{n1} & x_{n2} & \cdots & x_{np}
\end{pmatrix}
$ where $n$ is the number of *examples* and $p$ is the number of *features*.

*Features* are called *variables* in the book.


*\<missing part\>* ... because my laptops battery died and I didn't save :(

---

### Inference

*Inference* is the statistical term for *Data Mining*.
Instead of building a *model* with the goal of *prediction* the model is built with the goal to understand how $X_1, ..., X_p$ affect $Y$.
*f* can not be treated as a black box because we need to know its exact form.
Following question may be answered:
- Which are the most relevant features for a decision?
- What is the relationship (e.g. positive/negative) between *response* ($Y$) and *predictor* ($X_1, ..., X_p$)

##### Example
In Advertising: Where the *dataset* consists of *features* in form of spendings on advertisement per media and *labels* in form of the amount of sales.
-  Which media contributes most to sales.
- How much increase in sales is associated with a given increase in TV advertisement?
---
## How do we estimate $f$?

### Parametric Methods
2 Steps:
  1. We make an assumption about the form or shape of $f$ (the *model*). FOr example that $f$ is linear in $X$: $$f(X)=\beta_0+\beta_1X_1+\beta_2X_2+\ldots+\beta_pX_p$$. Once we assumed that $f$ is linear, all we have to do is to estimate the coefficients $\beta_0, \beta_1, \ldots, \beta_p$
  2. After a *model* has been selected we nee a procedure or *learning algorithm* that uses the *training data* to *fit* or *train* the *model*. That is, we want to estimate the parameters $\beta_0, \beta_1, \ldots, \beta_p$. That is, we want to find values of these parameters such that $$Y\approx \beta_0+\beta_1X_1+\beta_2X_2+\ldots+\beta_pX_p$$. The most common approach referred to as *(ordinary) least squares*

The *parametric* approach to estimating the *model* $f$ reduces the problem down to estimating a set of parameters, which is much easyer than the problem of estimating an entirely arbitrary function $f$.

### Non-parametric methods

Non-parametric methods do not make explicit asumptions about the functional form or shape of $f$.

---
