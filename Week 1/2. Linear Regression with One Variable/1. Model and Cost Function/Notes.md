# Linear Regression

- [Linear Regression](#linear-regression)
  - [The Cost Function](#the-cost-function)
  - [Cost function intuition](#cost-function-intuition)
  - [Cost Function Intuition II](#cost-function-intuition-ii)

[figure1]: ./figure1.bmp
[figure2]: ./figure2.bmp
[figure3]: ./figure3.bmp
[figure4]: ./figure4.bmp
[figure5]: ./figure5.bmp
[figure6]: ./figure6.bmp

Notation:

> $m$ = Number of  training examples
> 
> $x's$ = "input" variable / features
>
> $y's$ = "output" variable / "target" variable
>
> ($x$,$y$) = one training example
> 
> ($x^i$,$y^i$) = x and y at the i'th row in the table

$x^i$ is our input variable and $y^i$ is our output.

$m$ is called a training set.

To describe the supervised learning problem slightly more formally, our goal is, 
given a training set, to learn a function h : X → Y so that h(x) is a “good” 
predictor for the corresponding value of y. For historical reasons, this function h 
is called a hypothesis. 

Hypothesis: $h_\theta (x) = \theta_0 + \theta_1x$

![alt text][figure1]

When the target variable that we’re trying to predict is continuous, such as in our 
housing example, we call the learning problem a **regression** problem. When y can take 
on only a small number of discrete values (such as if, given the living area, we 
wanted to predict if a dwelling is a house or an apartment, say), we call it a 
**classification** problem.

Example Training set:

| size in feet$^2$ ($x$)  | Price (\$) in 1000's ($y$)  |
|---|---|
|  2104 |  460 |
|  1416 |  232 |
|  1534 |  315 |
|  852  |  178 |
|  ...  | ...  |


## The Cost Function

Hypothesis: $h_\theta (x) = \theta_0 + \theta_1x$

Idea: Choose $\theta_0$, $\theta_1$ so thay $h_\theta(x)$ is close to $y$ for our
training examples $(x,y)$

We can measure the accuracy of our hypothesis function by using a **cost function**. 
This takes an average difference (actually a fancier version of an average) of all the 
results of the hypothesis with inputs from x's and the actual output y's.

Minimize $\theta_0 \theta_1$

Remember that $m$ is the number of training examples.

Hypothesis:
$$h_\theta(x^i) = \theta_0 + \theta_1 x^i$$

**Cost function** (Squared error function or Mean squared error):
$$J(\theta_0, \theta_1) = \frac{1}{2m} * \sum_{i=1}^{m}(h_\theta(x^i) - y^i) ^ 2$$

To break it apart, it is $\frac{1}{2}\bar{x}$ where $\bar{x}$ is the mean of the 
squares of $h_\theta (x_{i}) - y_{i}$​, or the difference between the predicted value 
and the actual value.

This function is otherwise called the "Squared error function", or "Mean squared 
error". The mean is halved $\left(\frac{1}{2}\right)$ as a convenience for the 
computation of the gradient descent, as the derivative term of the square function will 
cancel out the $\frac{1}{2}$ term. The following image summarizes what the cost 
function does: 

![alt text][figure2]

## Cost function intuition

Recap:

> Hypothesis: $h_\theta(x) = \theta_0 + \theta_1 x$
>
> Parameters: $\theta_0,\theta_1$
> 
> Cost Function: $J(\theta_0, \theta_1) = \frac{1}{2m} * \sum_{i=1}^{m}(h_\theta(x^i) - y^i) ^ 2$
> 
> Goal: $minimize$ $\theta_0,\theta_1 J(\theta_0,\theta_1)$

Simplified:

> Hypothesis: $h_\theta(x) = \theta_1 x$
> 
> Parameters: $\theta_1$
> 
> Cost function: $J(\theta_1) = \frac{1}{2m} * \sum_{i=1}^{m}(h_\theta(x^i) - y^i) ^ 2$
>
> Goal: $minimize$ $\theta_1 J(\theta_1)$

Example:

Suppose we have a training set with $m=3$ examples, plotted below. Our hypothesis representation is $h_\theta(x) = \theta_1x$, with parameter $\theta_1$​. The cost function $J(\theta_1)$ is $J(\theta_1) = \frac{1}{2m} \sum^m_{i=1} (h_\theta (x^{(i)}) - y^{(i)})^2$. What is $J(0)$?

![alt text][figure3]

Since $\theta_1 = 0$ then $h_\theta(x) = 0x = 0$

We get:

$J(0) = \frac{1}{2(3)} [(0 - 1)^2 + (0 - 2)^2 + (0 - 3)^2]$

$= \frac{1}{6} [1 + 4 + 9]$

$= \frac{1}{6} [14]$

$= \frac{14}{6}$

---

If we try to think of it in visual terms, our training data set is scattered on the x-y plane. We are trying to make a straight line 

(defined by $h_\theta(x)$ which passes through these scattered data points. 

Our objective is to get the best possible line. The best possible 
line will be such so that the average squared vertical distances of 
the scattered points from the line will be the least. Ideally, the 
line should pass through all the points of our training data set. In 
such a case, the value of $J(\theta_0, \theta_1)$
will be 0. The following example shows the ideal situation where we 
have a cost function of 0. 

![alt text][figure4]

When $\theta_1 = 1$, we get a slope of 1 which goes through every 
single data point in our model. Conversely, when $\theta_1 = 0.5$, we 
see the vertical distance from our fit to the data points increase. 

![alt text][figure5]

This increases our cost function to 0.58. Plotting several other 
points yields to the following graph: 

![alt text][figure6]

Thus as a goal, we should try to minimize the cost function. In this 
case, $\theta_1 = 1$ is our global minimum. 

---

## Cost Function Intuition II

