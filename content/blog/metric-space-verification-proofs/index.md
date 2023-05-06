---
title: "Metric Space Verification Proofs"
date: 2023-04-22
slug: "metric-space-verification-proofs"
description: "Some "
keywords: ["metric space", "proof"]
draft: false
tags: ["maths"]
math: true
toc: true
---

## What is a metric space?

In the study of mathematical (real) analysis, metric space is a commonly covered topic in typical university curricula.

A [metric space](https://en.wikipedia.org/wiki/Metric_space) can be said as a notion that produces a special kind of collection such that we can describe the _distance_ or _length_ between two elements in the collection using a certain function. A formal name of such function is _metric_. 

Formally, a metric space is defined as a pair $(S,d)$, where $S$ is a set and $d : S \times S \rightarrow \mathbb{R}$ is a metric associated with $S$.

For $(S,d)$ to be a metric space, the metric $d$ should satisfy the following key properties:
- Positivity: $d(x,y)$ is _nonnegative_[^1], i.e. $d(x,y) \geqslant 0$, for all $x, y \in S$.

- Definiteness: $d(x,y) = 0$ if and only if $x=y$, for all $x, y \in S$.

- Symmetry: $d(x,y)=d(y,x)$, for all $x, y \in S$.

- [Triangle Inequality](https://en.wikipedia.org/wiki/Triangle_inequality): $d(x,y) \leqslant d(x,z)+d(z,y)$, for all $x,y,z \in S$.

## Verification proofs of common metric spaces

There are some metric spaces which are commonly seen in most real analysis textbooks. 

In this section, we verify that they indeed are metric spaces. To show that a given pair of set and metric $(S,d)$ is a metric space, we can show that it satisfies all four key properties as outlined above.

### Usual metric space

First, we have the set of real numbers associated with the _usual metric_ $d : \mathbb{R} \times \mathbb{R} \rightarrow \mathbb{R}$, i.e. the pair $(\mathbb{R},d)$ where $d$ is given by $d(x,y)=\vert{x-y}\vert$ for all $x,y \in \mathbb{R}$.

Here, we show that $(\mathbb{R},d)$ is a metric space. 
- Positivity: This follows from the properties of absolute values.

- Definiteness: This follows from the fact that the absolute value of a number is zero if and only if the number itself is zero.

- Symmetry: This follows from the symmetry of the absolute value of two substracted terms, i.e. $|a-b|=|b-a|$.

- Triangle Inequality: This follows from the fact that $|a-c|=|(a-b)+(b-c)| \leqslant |a-b|+|b-c|$.

### Euclidean metric space

Next, we have the set of the [Cartesian product](https://en.wikipedia.org/wiki/Cartesian_product) of $n$ copies of the set of real numbers, $\mathbb{R}^n$, endowed with the _Euclidean metric_ $d_E : \mathbb{R}^n \times \mathbb{R}^n \rightarrow \mathbb{R}$, which is given by $d_E(x,y)=\sqrt{\sum_{i=1}^{n}{(x_i-y_i)^2}}$ for all $x = (x_1,x_2,\ldots,x_n), y=(y_1,y_2,\ldots,y_n) \in \mathbb{R}^n$.

We show that $(\mathbb{R}^n,d_E)$ is a metric space.
- Positivity: This follows from the fact that the sum of squares are nonnegative and its square root is also nonnegative.

- Definiteness: This follows from the fact that a square is zero if and only if the squared term itself is zero.

- Symmetry: This follows from the symmetry of the square of subtraction, i.e. $(a-b)^2=(b-a)^2$ for any $a,b \in \mathbb{R}$.

- Triangle Inequality: This follows from the [Cauchy-Schwarz inequality](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Schwarz_inequality).

### 'Manhattan metric space'

_I put quotation marks around the name because I don't think it is a universally accepted name._

Consider the pair $(\mathbb{R}^n,d_M)$, where $d_M : \mathbb{R}^n \times \mathbb{R}^n \rightarrow \mathbb{R}$ is given by $d_M(x,y)=\sum_{i=1}^{n}{\vert{x_i-y_i}\vert}$. Such metric is commonly known as the [Manhattan distance function](https://en.wikipedia.org/wiki/Taxicab_geometry).

We verify that $(\mathbb{R}^n,d_M)$ is a metric space.
- Positivity: This follows from the fact that absolute values are nonnegative.

- Definiteness: This follows from the fact that the absolute value of a term is zero if and only if the term itself is zero.

- Symmetry: This follows from the fact that for any $a, b \in \mathbb{R}$, $|a-b|=|b-a|$.

- Triangle Inequality: This follows from the Triangle Inequality involving absolute values.

### Discrete metric space

There is also a metric space that is not limited by the choice of sets.

Let $S$ be an arbitrary non-empty set. For all $x,y \in S$, we define a _discrete metric_ $d : S \times S \rightarrow \mathbb{R}$ by $$d(x,y) = \begin{cases} 0 & \text{if } x = y, \newline 1 & \text{if } x \neq y. \end{cases}$$

We verify that $(S,d)$ is a metric space.
- Positivity: For any two real numbers, either they are equal to each other or they are not. Since both cases are mapped to a nonnegative value by the metric, positivity is satisfied.

- Definiteness: This follows immediately from the definition of the metric.

- Symmetry: This follows immediately from the definition of the metric.

- Triangle Inequality: Fix any two numbers $a,b \in \mathbb{R}$. If $a=b$, then $d(a,b)=0 \leqslant d(a,c)+d(c,b)$ since both terms of the right-hand side of the inequality are nonnegative, so the triangle inequality is satisfied for this case. If $a \neq b$, then $d(a,b)=1$. Take another number $c$. Since $a \neq b$, we can only have at most one equality for between $a$ and $c$ and between $b$ and $c$, so $d(a,c)+d(c,b) \geqslant 1 = d(a,b)$, and thus the triangle inequality is satisfied for this case too. Since two numbers are either equal or not equal, this proves the triangle inequality for the general case.

[^1]: I'd say this term choice is slightly misleading, but it has become the default convention in the literature anyways.