# Parameter Learning

- [Parameter Learning](#parameter-learning)
  - [Gradient descent](#gradient-descent)
  - [Gradient descent algorithm](#gradient-descent-algorithm)
  - [Gradient descent intuition](#gradient-descent-intuition)
  - [Greadient descent for linear regression](#greadient-descent-for-linear-regression)

[figure1]: ./figure1.bmp
[figure2]: ./figure2.bmp

## Gradient descent

![alt text][figure1]

We have some function $J(\theta_0,\theta_1)$

We want $\underset{\theta_0,\theta_1}{min} J(\theta_0,\theta_1)$

**Outline**:

* Start with some $\theta_0,\theta_1$
* Keep changing $\theta_0,\theta_1$ to reduce $J(\theta_0,\theta_1)$
  until we hopefully end up at a minimum

## Gradient descent algorithm

*Notes*:

* := indicates the assignment operator (a := b, take value of b, store it in a)
* $\alpha$ is the leaning rate,controls how big of a step we take down with gradient descent
  

> repeat until convergence {
> 
>   $\theta_j := \theta_j - \alpha \frac{\partial}{\partial\theta_j}J$ 
>   $(\theta_0,\theta_1)$
>   (for $j = 0$ and $j = 1$ ($\theta_0,\theta_1$))
> 
> }
>
> Simultaneously update $\theta_0$ and $\theta_1$
> 
> ---
> Implementation:
> 
> Correct : Simultaneous update
> 
> $temp0 := \theta_0 - \alpha \frac{\partial}{\partial\theta_0}J(\theta_0,\theta_1)$
> 
> $temp1 := \theta_1 - \alpha \frac{\partial}{\partial\theta_1}J(\theta_1,\theta_1)$
> 
> $\theta_0 := temp0$
> 
> $\theta_1 := temp1$


**Example**:

Suppose $\theta_0= 1, \theta_1= 2$, and we simultaneously update $\theta_0$ and 
$\theta_1$​ using the rule: $\theta_j := \theta_j + \sqrt{\theta_0 \theta_1}$
(for j = 0 and j=1) 

What are the resulting values of $\theta_0$​ and $\theta_1$​?

$temp0 := 1 + \sqrt{1 * 2} = 1 + \sqrt{2}$

$temp1 := 2 + \sqrt{1 * 2} = 2 + \sqrt{2}$

$\theta_0 := temp0 = 1 + \sqrt{2}$

$\theta_1 := temp1 = 2 + \sqrt{2}$

## Gradient descent intuition

How does gradient descent converge with a fixed step size $\alpha$?

The intuition behind the convergence is that $\frac{d}{d\theta_1} J(\theta_1)$ approaches 0 as we approach the bottom of our convex function. At the minimum, the derivative will always be 0 and thus we get:

$\theta_1:=\theta_1-\alpha * 0$

![alt text][figure2]

## Greadient descent for linear regression

> $\frac{\partial}{\partial\theta_j}J(\theta_0,\theta_1)$
> $=$
> $\frac{\partial}{\partial\theta_j} * \frac{1}{2m}$
> $\sum_{i=1}^{m}(h_\theta(x^{(i)} )- y^{(i)})^2$ 
> 
> $=$
> $\frac{\partial}{\partial\theta_j} * \frac{1}{2m}$
> $\sum_{i=1}^{m}(\theta_0 + \theta_1 x^{(i)} - y^{(i)})^2$ 

Results of the derivatives:

> $j = 0: \frac{\partial}{\partial\theta_0}J(\theta_0,\theta_1)$
> $=$
> $\frac{1}{m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})$
> 
> $j = 1: \frac{\partial}{\partial\theta_1}J(\theta_0,\theta_1)$
> $=$
> $\frac{1}{m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)}) * x^{(i)}$

The gradient descent algorithm can now be written as:

> repeat until convergence {
> 
> $\theta_0 := \theta_0 - \alpha * \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})$
> 
> $\theta_1 := \theta1 - \alpha * \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)}) * x^{(i)}$
> 
> }

It turns out that our cost function $J(\theta_0,\theta_1)$ 
is always going to be a convex function (bow shaped).
This means the gradient descent will always find the correct minimum. 