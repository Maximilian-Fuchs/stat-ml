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
  1. We make an assumption about the form or shape of $f$ (the *model*). FOr example that $f$ is linear in $X$: $$f(X)=\beta_0+\beta_1X_1+\beta_2X_2+\ldots+\beta_pX_p.$$Once we assumed that $f$ is linear, all we have to do is to estimate the coefficients $\beta_0, \beta_1, \ldots, \beta_p$
  2. After a *model* has been selected we nee a procedure or *learning algorithm* that uses the *training data* to *fit* or *train* the *model*. That is, we want to estimate the parameters $\beta_0, \beta_1, \ldots, \beta_p$. That is, we want to find values of these parameters such that $$Y\approx \beta_0+\beta_1X_1+\beta_2X_2+\ldots+\beta_pX_p.$$The most common approach referred to as *(ordinary) least squares*

The *parametric* approach to estimating the *model* $f$ reduces the problem down to estimating a set of parameters, which is much easyer than the problem of estimating an entirely arbitrary function $f$.

### Non-parametric methods

- Non-parametric methods do not make explicit asumptions about the functional form or shape of $f$.
- They serve as a universal function approximator, therefore they can potentially describe data way better than models that are constrained by an assumption.
- **But**
	- They need more data to be trained. I.e. Far more observations are needed in order to obtain an accurate estimate for $f$.
	- Also they are much more interpretable and therfore more suitable for *inference*

---
### Regression Versus Classification Problems

Variables can be characterized as either *quantitative* or *qualitative* (also known as *categorical*).
- Quantitative variables take on numerical value such as height or income.
- Qualitative variables take on values in one of K different *classes* such as male/female or yes/no.
- Problems with a *quantitative response* (*label*) are referred to as **regression**
- Problems with a *qualitative response* (*label*) are reffered to as **classification**

---
### Estimating Performance
Most common measure is *mean squared error* (MSE) $$MSE=\frac{1}{n}\sum_{i=1}^{n}{(y_i-\hat{f}(x_i))^{2}}.$$We need to differ between *training error* and *test error*. The *training error* tells us how good a model describes the training data. But In reality we almost always want to know how good a model describes unseen examples. (See Overfitting Problem and Bias/Variance Tradeoff)

(Some Notes missing)

---
### Bias Variance Tradeoff
The expected test MSE for a given value $x_0$ can always be decomposed into the sum of three fundamental quantities: $$E(y_0-\hat{f}(x_0))^2=Var(\hat{f}(x_0))+[Bias(\hat{f(x_0)})]^2+Var(\epsilon).$$Where $E(y_0-\hat{f}(x_0))^2$ refers to the average test MSE that we would obtain if we repeatedly estimated $f$ using a large number of training sets and tested each at $x_0$.
The Overall expected test MSE can be computed by averaging $E(y_0-\hat{f}(x_0))^2$ over all possible values in the test set.
In order to get a good preiction model we need to select a *statistical learning method* (*learning algorithm*) that simultaneously achieves *low variance* and *low bias*.

##### Variance
Refers to the amount by which $\hat{f}$ will change if we estimated it, using a different training set.
Ideally the estimate for $f$ should not vary to much between training sets.
If a model has *high variance* small changes in the training data canresult in large changes in $\hat{f}$.
In general more flexible statistical methods have higher variance.

##### Bias
*Bias* refers to the error that is introduced by approximating a complicated problem by a much simpler model.

---
### The Classification Setting

The difference to regression problems is that the _response_ (_label_) is _qualitative_ instead of _quantitative_. That means the _response_ can have one of _n_ values from a set of values.

#### Error

The error for a classification problem is commonly calculated with the _error rate_: $$E=\frac{1}{n}\sum_{i=1}^{n}{I(y_i\neq\hat{y}_i)}$$ where $I(y_i \neq \hat{y}_i)$ stands for the indicator variable that is 1 if $y_i \neq \hat{y}_i$ an 0 otherwise.

#### Classification Goals

- Build a classifier $C(X)$ that assigns a label from a set of labels to an unseen example $X$

- Assess the uncertainty in each classification

- Understand the roles of the different _predictors_ (_features_) among $X=(X_1, X_2, \ldots, X_p)$ 
	- i.e. Find out which feature contributes most to the decision. (See *inference*)

---

#### The Bayes Classifier

A simple classifier can be implemented by assigning each *observation* (*unlabled example*) the most likely class given it's *predicor values* (*feature values*).

$$max(Pr(Y=j|X=x_0))$$ Where $j$ is a class, $x_0$ is a given *feature vector*. Calculate the *conditional probability* for all classes and choose the class where the *conditional probability* is largest.


###### Example

If we have only 2 classes ($j\in{1,2}$) the *Bayes Classifier* predicts class $1$ if $Pr(Y=1|X=x_0) > 0.5$ and class $2$ otherwise.
The *Bayes decision boundary* is at each value of $x$ where the *conditional probability* is exactly $0.5$. 

###### Bayes Error Rate

*skipped*

something like: $1 - 1/N \sum_{n=0}^{N}{max_j Pr(Y=j|X=x_n)}$, meaning the difference to 1 for the Probability of the predicted class. Which is equal to the *irreducable error*

---

































































---

#### Learning Algorithms
| Name | Supervised/Unsupervised | Regression/Classification | Interpretable/Accurate | Parametric/Non-Parametric |
| --- | --- | --- | --- | --- | --- |
| Logistic Regression | Supervised | Classification |  |   |   |
| Least squares linear regression | Supervised | Regression | Interpretable | Parametric |   |
| Thin-plate Spline | - | - | - | Non-parametric |   |
| K-Nearest Neighbor | Unsupervised | Classification | Interpretable | - |   |
| Lasso | Supervised |   |   |   |   |

---

#### Questions

- What is the difference between Likelihood and Probability? (Does the most likely class mean it is the class witrh the highest probability given its *predictors* (*features*)?)

