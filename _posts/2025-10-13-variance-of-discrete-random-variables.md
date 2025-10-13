---
title: "Variance of Discrete Random Variables"
excerpt_separator: "<!--more-->"
categories:
  - math
tags:
  - math
  - statistics
  - probability
  - random variables
---

# Background
In the textbook "**Applied Statistics and Probability for Engineers**" 7edition by Montgomery and Runger, chapter 3, Discrete Random Variables and Probability Distributions, some basic concepts are introduced as follows.

This post is a note to prove the equation (3.6b) for the variance of discrete uniform distributions.

## 3.1 Probability Distributions and Probability Mass Functions

- Probability Mass Function: For a discrete random variable $X$ with possible values $x_{1}$, $x_{2}$, $x_{3}$, . . . , $x_{n}$,  a probability mass function is a function that:
	- $f(x_{i} \ge 0)$
	- $\sum_{i=1}^{n}f(x_{i}) = 1$
	- $f(x_{i}) = P(X = x_{i})$

## 3.2 Cumulative Distribution Functions

## 3.3 Mean and Variance of Discrete Random Variables

- The mean or expected value of the discrete random variable $X$, denoted as $\mu$ or $E(X)$, is 

  $$
  \mu = E(X) = \sum_{x}xf(x) \tag{3.3}
  $$
  

- The variance of $X$, denoted as $\sigma^2$ or $V(X)$, is

$$
\sigma^2 = V(X) = E(X-\mu)^2 = \sum_{x}(x-\mu)^2f(x) = \sum_{x}x^2f(x)-\mu^2
$$

## 3.4 Discrete Uniform Distributions

- Discrete Uniform Distribution:
	- A random variable $X$ has a discrete uniform distribution if each of the $n$ values in its range,  $x_{1}$, $x_{2}$, $x_{3}$, . . . , $x_{n}$,  has equal probability, Then

$$
f(x_{i})= \frac{1}{n} \tag{3.5}
$$

- Mean and Variance

$$
\mu = E(X) = \frac{b+a}{2} \tag{3.6a}  
$$

$$
\begin{equation}
\sigma^2 = \frac{(b-a+1)^2-1}{12} 
\tag{3.6b}
\end{equation}
$$



---

**Proof** of $(3.6b)$ :

$$
\sigma^2 =  \sum_{x=a}^{b} x^2 f(x) - \mu^2 = \sum_{k=a}^{b} k^2\frac{1}{b-a+1}-(\frac{b+a}{2})^2
$$

The key here is to calculate:  

$$
\sum_{k=a}^{b} k^2 = a^2 + (a+1)^2 + \dots + (a+n)^2
$$

where $n = b-a$, and $1^2+2^3+\dots+n^2=\frac{1}{6}n(n+1)(2n+1)$, so[^1]

$$
\begin{align}
\sum_{k=a}^{b} k^2 = (n+1)a^2 + 2(1+2+\dots+n)a + (1^2+2^2+\dots+n^2)\\ 

 = (n+1)a^2+n(n+1)a+\frac{1}{6}n(n+1)(2n+1) 
 \end{align}
$$

Now we have:

$$
\sigma^2 =\frac{1}{n+1}[(n+1)a^2+n(n+1)a+\frac{1}{6}n(n+1)(2n+1) ] -(\frac{b+a}{2})^2
$$

and $n = b-a$. This leads to:

$$
\begin{align}
\sigma^2 =\left[a^2+(b-a)a+\frac{1}{6}((b-a)(2b-2a+1) \right] \\
-(\frac{b+a}{2})^2 
 \\
= \left[(ba+\frac{1}{3}(b-a)^2+\frac{1}{6}(b-a) \right]-(\frac{b+a}{2})^2\\
= \frac{1}{2}ab+\frac{1}{12}(a^2+b^2)-\frac{2}{3}ab+\frac{1}{6}(b-a)\\   \\
= \frac{1}{12}(a^2+b^2)-\frac{1}{6}ab+\frac{1}{6}(b-a)\\
= \frac{1}{12}(b-a)^2+\frac{1}{6}(b-a)+\frac{1}{12}-\frac{1}{12}\\
= \frac{(b-a+1)^2-1}{12} \\
\end{align}
$$

Q.E.D.

[^1]: A proof of $1^2+2^3+\dots+n^2=\frac{1}{6}n(n+1)(2n+1)$ can be found here: [What are some ways to prove that \[math\]1^2+2^2+\\cdots + n^2 = \\frac {n(n+1) (2n+1)} {6}\[/math\]? - Quora](https://qr.ae/pCv3zl), this answer actually is not original. For example, an early version can be found in the book "**Proofs Without Words: Exercises in Visual Thinking**".

