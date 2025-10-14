---
title: "Geometric and Negative Binomial Distribution"
excerpt_separator: "<!--more-->"
categories:
  - math
tags:
  - math
  - statistics
  - probability
  - random variables
---

## Background
In the textbook "*Applied Statistics and Probability for Engineers*" 7edition by Montgomery and Runger, chapter 3, *Discrete Random Variables and Probability Distributions*, some basic concepts are introduced.

This post presents a derivation of equation (3.10b), (3.12a), (3,12b), which are variance of geometric random variable, mean of negative binomial random variable and variance of negative binomial random variable, respectively. 


## Geometric Distribution

In a series of Bernoulli trials (independent trials with constant probability $p$ of a success), the random variable $X$ that equals the number of trials until the first success is a geometric random variable with parameter $0 < p < 1$ and 


$$
f(x) = (1-p)^{x-1}p  \qquad  x = 1, 2, \dots \tag{3.9}
$$
- Mean of a geometric random variable
  
$$
\mu = \sum_{k=1}^{\infty} kp(1-p)^{k-1} = p \sum_{k=1}^{\infty} kq^{k-1} = p\frac{\partial }{\partial q}\sum_{k=1}^{\infty} q^k
$$


where $q=1-p$.  so that


$$
\mu = p \frac{\partial}{\partial} \left| \frac{q}{1-q} \right| = \frac{p}{(1-q)^{2}} = \frac{1}{p} \tag{3.10a}
$$
- Variance of a geometric random variable
  
$$
\sigma^2 = V(X) = E(X^2) - (E(X))^2 = \sum x^2f(x) - \mu^2 = \sum x^2f(x) - \frac{1}{p^2}
$$

since 

$$
\sum x^2f(x) = \sum_{k=1}^{\infty}k^2p(1-p)^{k-1} = p\sum_{k=1}^{\infty} k^2q^{k-1}
$$

here $q = 1-p$ and considering $k^2=(k+1)k -k$, we have

$$
\begin{align}
p\sum_{k=1}^{\infty} k^2q^{k-1} = p\sum_{k=1}^{\infty}\left(\frac{\partial^2}{\partial q^2} q^{k+1} - \frac{\partial}{\partial q}q^{k} \right) = p\left(\frac{\partial^2}{\partial q^2}\frac{q^2}{1-q} - \frac{\partial}{\partial q}\frac{q}{1-q} \right)\\ \\
= p\left( \frac{2}{p^3} - \frac{1}{p^2} \right) = \frac{2}{p^2}-\frac{1}{p}
\end{align}
$$

so that

$$
\sigma^2 =  \frac{2}{p^2}-\frac{1}{p} - \frac{1}{p^2} = \frac{1-p}{p^2} \tag{3.10b}
$$


Q.E.D.

## Negative Binomial Distribution

In a series of Bernoulli trials (independent trials with constant probability $p$ of a success), the random variable $X$ that equals the number of trials until $r$ successes occur is a *negative binomial random variable* with parameters $0 < p < 1$ and $r = 1, 2, 3, \dots$ , and 

$$
f(x) = \binom{x-1}{r-1}(1-p)^{x-r}p^r \qquad x = r, r+1, r+2, \dots \tag{3.11}
$$

Because at least $r$ trials are required to obtain $r$ successes, the range of $X$ is from $r$ to $\infty$. 

### Tips

- Special case for $r = 1$, a *negative binomial random variable* is a *geometric random variable*.
- General case for $r \neq 1$, *negative binomial random variable* represented as *a sum of geometric random variables*.
	- Let $X$ denote the total number of trials required to obtain $r$ successes. Let $X_{1}$ denote the number of trials required to obtain the first success, $X_{2}$ the second, and etc. Then the total number of trials required to obtain $r$ successes is $X = X_{1} + X_{2} + \dots + X_{r}$. Because of the lack of memory property, each of the random variable $X_{1}, X_{2}, \dots,X_{r}$ has a geometric distribution with the same value of $p$. Consequently, a negative binomial random variable can be interpreted as the sum of $r$ geometric random variables. Illustrated in Figure 3.10.
	- Based on above, we can say $\mu = \frac{r}{p}$, and $\sigma^2 = \frac{r(1-p)}{p^2}$, just $r$ times the values of geometric random variables as equation (3.12) shows.

### Mean of negative binomial random variable: (direct calculation of (3.12a))



$$
\begin{align}
\mu = E(X) = \sum xf(x) = \sum_{k=r}^{\infty} \binom{k-1}{r-1}(1-p)^{k-r}p^r = \sum_{k=r}^{\infty} \frac{k!}{(k-r)!(r-1)!}(1-p)^{k-r}p^r \\ \\
= \frac{p^r}{(r-1)!} \sum_{k=r}^{\infty} \frac{k!}{(k-r)!}q^{k-r}= \frac{p^r}{(r-1)!} \sum_{k=r}^{\infty} \frac{\partial^r}{\partial q^r}q^{k} = \frac{p^r}{(r-1)!} \frac{\partial^r}{\partial q^r}\sum_{k=r}^{\infty} q^{k} \\
= \frac{p^r}{(r-1)!}\frac{\partial ^r}{\partial q^r}\left( \frac{q^r}{1-q} \right) = \frac{p^r}{(r-1)!}\frac{\partial ^r}{\partial q^r}\left( \frac{q^r-1+1}{1-q}\right) \\
= \frac{p^r}{(r-1)!}\frac{\partial ^r}{\partial q^r}\left[-\left(\frac{1-q^r}{1-q}\right)+\left(\frac{1}{1-q} \right)\right]
\end{align}
$$

here as we know $\frac{1-q^r}{1-q} = 1 + q + q^2 + \dots + q^{r-1}$, so the $r$-order partial derivative is $0$, and then: 

$$
\mu = \frac{p^r}{(r-1)!}\frac{\partial^r}{\partial q^r}\left(\frac{1}{1-q}\right) = \frac{p^r}{(r-1)!} \frac{r!}{p^{r+1}} = \frac{r}{p} \tag{3.12a}
$$


Q.E.D.

### Variance of negative binomial random variable: (direct calculation of (3.12b))



$$
\sigma^2 = \sum_{k=r}^{\infty} k^2\binom{k-1}{r-1}(1-p)^{k-r}p^r - \frac{r^2}{p^2} = \sum_{k=r}^{\infty} \frac{kk!}{(k-r)!(r-1)!}(1-p)^{k-r}p^r - \frac{r^2}{p^2}
$$



since $kk! = (k+1)! - k!$, we have

$$
\begin{align}
\sigma^2 = \sum_{k=r}^{\infty} \left(\frac{(k+1)!}{(k-r)!(r-1)!}(1-p)^{k-r}p^r - \frac{k!}{(k-r)!(r-1)!}(1-p)^{k-r}p^r \right) - \frac{r^2}{p^2}  \\
= \frac{p^r}{(r-1)!}\sum_{k=r}^{\infty} \left( \frac{(k+1)!}{(k-r)!}q^{k-r} - \frac{k!}{(k-r)!}q^{k-r} \right) - \frac{r^2}{p^2} \\
= \frac{p^r}{(r-1)!}\sum_{k=r}^{\infty} \left(\frac{\partial^{r+1}}{\partial q^{r+1}}q^{k+1}- \frac{\partial^{r}}{\partial q^{r}}q^{k}\right) - \frac{r^2}{p^2} \\
= \frac{p^r}{(r-1)!}\left[\frac{\partial^{r+1}}{\partial q^{r+1}}\left(\frac{q^{r+1}}{1-q}\right)-\frac{\partial^{r}}{\partial q^{r}}\left(\frac{q^r}{1-q}\right)\right]- \frac{r^2}{p^2} 
\end{align}
$$


as we already proved


$$
\frac{\partial ^r}{\partial q^r}\left(\frac{q^r}{1-q}\right) = \frac{r!}{p^{r+1}}
$$


similarly, 


$$
\frac{\partial^{r+1}}{\partial q^{r+1}}\left(\frac{q^{r+1}}{1-q}\right) = \frac{(r+1)!}{p^{r+2}}
$$


So that


$$
\sigma^2 = \frac{p^r}{(r-1)!}\left(\frac{(r+1)!}{p^{r+2}}-\frac{r!}{p^{r+1}}\right) - \frac{r^2}{p^2} = \frac{(r+1)r}{p^2} - \frac{r}{p} -\frac{r^2}{p^2} = \frac{r(1-p)}{p^2} \tag{3.12b}
$$


Q.E.D.