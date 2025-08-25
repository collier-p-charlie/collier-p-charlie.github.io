---
title: Introduction to Logic
date: 2025-08-25
description: >
  An introduction to basic logic concepts and mathematical logic in the real numbers.
categories: 
  - Analysis
---

# Introduction to Logic

Before getting into the study of analysis, we need to understand some basic concepts in logic.
Indeed, logic is the foundation of all mathematical reasoning, and it will be used extensively through this blog series.

## Logical Connectives

In logic, a _statement_ is an assertion which is either _true_ **T** or _false_ **F**, but not both.
For example, the statement $1 > 0$ is **T** and $1 = 2$ is **F**. 
Now suppose we have generic statements $P$, $Q$ and $R$, then we can construct compound statements using _logical connectives_.
For example, we have the following:

1. _Conjunction_, denoted by $P \land Q$, which is _true_ if and only if both $P$ and $Q$ are _true_, and _false_ otherwise;
2. _Disjunction_, denoted by $P \lor Q$, which is _true_ if and only if $P$ or $Q$ or both are _true_;
3. _Implication_, denoted by $P \Rightarrow Q$, which is _true_ unless $P$ is _true_ and $Q$ is _false_; and
4. _Negation_, denoted by $\neg P$, which is _true_ if and only if $P$ is _false_.

These logical connectives can be defined using _truth tables_ as follows:

|  $P$  |  $Q$  | $P \land Q$ | $P \lor Q$ | $P \Rightarrow Q$ | $\neg P$ |
|:-----:|:-----:|:-----------:|:----------:|:-----------------:|:--------:|
| **T** | **T** |    **T**    |   **T**    |       **T**       |  **F**   |
| **T** | **F** |    **F**    |   **T**    |       **F**       |  **F**   |
| **F** | **T** |    **F**    |   **T**    |       **T**       |  **T**   |
| **F** | **F** |    **F**    |   **F**    |       **T**       |  **T**   |

For more reading on this, see [here](https://en.wikipedia.org/wiki/Logical_conjunction).
We note that the implication $P \Rightarrow Q$ can be interpreted as "_if $P$ then $Q$_", and is equivalent to $\neg P \lor Q$.
The _distributive_ and _de Morgan's_ laws are important properties of logical connectives, and are given as follows:

\begin{align*}
P \land (Q \lor R) &= (P \land Q) \lor (P \land R) \\
P \lor (Q \land R) &= (P \lor Q) \land (P \lor R) \\
\neg (P \land Q) &= \neg P \lor \neg Q \\
\neg (P \lor Q) &= \neg P \land \neg Q
\end{align*}

We can see how these work using _truth tables_ as above.

## Contrapositive

The _contrapositive_ of an implication $P \Rightarrow Q$ is defined as $\neg Q \Rightarrow \neg P$.
Both of these are _logically equivalent_, meaning we can prove either one is true - indeed, sometimes the _contrapositive_ is easier to prove.
Indeed, the truth table below shows the logical equivalence.

|  $P$  |  $Q$  | $P \Rightarrow Q$ | $\neg Q$ | $\neg P$ | $\neg Q \Rightarrow \neg P$ |
|:-----:|:-----:|:-----------------:|:--------:|:--------:|:---------------------------:|
| **T** | **T** |       **T**       |  **F**   |  **F**   |            **T**            |
| **T** | **F** |       **F**       |  **T**   |  **F**   |            **F**            |
| **F** | **T** |       **T**       |  **F**   |  **T**   |            **T**            |
| **F** | **F** |       **T**       |  **T**   |  **T**   |            **T**            |


## Universal and Existential Quantifiers
While we are here, we also define the _universal_ $\forall$ and _existential_ $\exists$ quantifiers:

- $\forall$ means _"for all"_ or _"for every"_;
- $\exists$ means _"there exists"_ or _"there is at least one"_; and
- $:$ means _"such that"_, sometimes also denoted simply as $s.t.$

Then if $P(x)$ is some statement involving the variable $x$, we can form the _universal statement_ $\forall x, P(x)$, which is _true_ if and only if $P(x)$ is _true_ for every possible value of $x$.
The logical negation of this statement $\neg (\forall x\, P(x))$ is equivalent to the _existential statement_ $\exists x: \neg P(x)$, which is _true_ if and only if there exists at least one value of $x$ such that $P(x)$ is _false_.

For example, $\forall x \in \mathbb{R}, x^2 \geq 0$ is _true_ (see [here](https://en.wikipedia.org/wiki/Real_number) for more information on $\mathbb{R}$).
Indeed, any real number squared is non-negative, e.g. $(-3)^2 = 9 \geq 0$ and $2^2 = 4 \geq 0$.
For the converse statement, consider $P(x)$ to be $x^3 > 0$ and $x$ to be any _real number_.
Then clearly if we look at any negative $x$, say $x = -1$, we have $P(x) = (-1)^3 = 1 < 0$, so there does exist an $x$ for which $\neg P(x)$ is _true_.

## Axioms

An _axiom_ is simply a statement that is taken to be _true_ without proof, and serves as a starting point for further reasoning and arguments.
Indeed, many mathematical systems are built upon a set of axioms.
For example, the _field_ and _order_ axioms of $\mathbb{R}$ are defined below.

### Field Axioms

These define the arithmetic properties of addition and multiplication within the set $\mathbb{R}$.
This includes properties like _commutativity_, _associativity_, _distributivity_, _identity_ elements ($0$ and $1$), and additive/multiplicative _inverses_.

| **Axiom ID** |                                            **Axiom**                                             |      **Description**      |
|:------------:|:------------------------------------------------------------------------------------------------:|:-------------------------:|
|      A1      |                   $\forall a, b, c \in \mathbb{R}, a + (b + c) = (a + b) + c$                    |   $+$ is _associative_    |
|      A2      |                           $\forall a, b \in \mathbb{R}, a + b = b + a$                           |   $+$ is _commutative_    |
|      A3      |             $\exists 0 \in \mathbb{R} : \forall a \in \mathbb{R}, a + 0 = a = 0 + a$             |    _additive identity_    |
|      A4      |        $\forall a \in \mathbb{R}\, \exists (-a) \in \mathbb{R} : a + (-a) = 0 = (-a) + a$        |    _additive inverse_     |
|      A5      |                         $\forall a, b, c \in \mathbb{R}, a(bc) = (ab)c$                          | $\times$ is _associative_ |
|      A6      |                              $\forall a, b \in \mathbb{R}, ab = ba$                              | $\times$ is _commutative_ |
|      A7      |        $\exists 1 \in \mathbb{R}\backslash \{0\} : \forall a \in \mathbb{R}, a1 = a = 1a$        | _multiplicative identity_ |
|      A8      | $\forall a \in \mathbb{R}\backslash \{0\} \exists a^{-1} \in \mathbb{R} : aa^{-1} = 1 = a^{-1}a$ | _multiplicative inverse_  |
|      A9      |                       $\forall a, b , c \in \mathbb{R}, a(b+c) = ab + ac$                        |     _distributivity_      |

The notation $A \backslash B$ is used to denote the set of elements in $A$ that are not in $B$.
So $\mathbb{R} \backslash \{0\}$ is the set of all real numbers except $0$.

### Order Axioms

These build on the _field_ axioms by introducing a notion of order (i.e., inequality) to the set $\mathbb{R}$.
For example, _trichotomy_ is that every number $x$ is either _negative_, _positive_ or $0$

| **Axiom ID** |                               **Axiom**                                |       **Description**       |
|:------------:|:----------------------------------------------------------------------:|:---------------------------:|
|     A10      |     $\forall a \in \mathbb{R}$ either $a < 0$, $a = 0$ or $a > 0$      | _trichotomy_ of _cardinals_ |
|     A11      |    $\forall a, b, c \in \mathbb{R}$ if $a < b$ then $a + c < b + c$    |                             |
|     A12      | $\forall a, b, c \in \mathbb{R}$ if $a < b$ and $c > 0$ then $ac < bc$ |                             |

For more information on _axioms_, see [here](https://en.wikipedia.org/wiki/Axiom).

## Examples

Using these axioms we can derive many useful properties of real numbers.

**Example 1.** The _additive identity_ $0$ in $\mathbb{R}$ is _unique_.

_Solution._ To prove this, we suppose there are two additive identities, say $0_A$ and $0_B$.
Then by **A3** we have that for any $a$ in $\mathbb{R}$ that $a + 0_A = a$ and $a + 0_B = a$.
Now letting $a = 0_B$ in the first equation gives $0_B + 0_A = 0_A$, and $a = 0_A$ in the second gives $0_A + 0_B = 0_A$.
Then using **A2** we see that $0_A = 0_B + 0_A = 0_A + 0_B = 0_B$, hence $0_A = 0_B$.
So if there were to exist two additive identities, we have just shown that they must be equal, hence _uniqueness_.

**Example 2.** For any $a,b \in \mathbb{R}$, if $ab = 0$ then either $a = 0$ or $b = 0$.

_Solution._ Suppose that $ab = 0$ but that $a \neq 0$ (_without loss of generality_ **WLOG**, since we could just relabel the variables).
Then by **A8** there exists a multiplicative inverse $a^{-1}$ such that $a^{-1}a = 1$ and so

\begin{align*}
a^{-1}(ab) = (a^{-1}a)b = 1b = b = 0
\end{align*}

**Example 3.** For any $a \in \mathbb{R}$, we have $-(-a) = a$.

_Solution._ That is, the additive inverse of the additive inverse of $a$ is just $a$ itself.
So for any $a \in \mathbb{R}$, axiom **A4** gives us an element $-a \in \mathbb{R}$ with $a + (-a) = 0 = (-a) + a$.
But since $(-a) \in \mathbb{R}$, axiom **A4** also gives us an element $-(-a) \in \mathbb{R}$ such that 

$$-(-a) + (-a) = 0 = (-a) + -(-a)$$

Then adding $-(-a)$ to both sides of the equation $a + (-a) = 0$, using **A1**/**A3** we see that 

\begin{align*}
(a + (-a)) + (-(-a)) = a + ((-a) + (-(-a))) = a + 0 &= a \\
0 + (-(-a)) &= -(-a)
\end{align*}

and both sides are equal.
A similar proof would show that $(a^{-1})^{-1} = a$ for any $a$.

**Example 4.** For any $a, b, c \in \mathbb{R}$, if $a + c = b + c$ then $a = b$.

_Solution._ There is an additive inverse $-c$ such that $c + (-c) = 0$ and so adding $-c$ to both sides of the equation and using associativity we see that

\begin{align*}
(a + c) + (-c) &= a + (c + (-c)) = a + 0 = a\\
(b + c) + (-c) &= b + (c + (-c)) = b + 0 = b
\end{align*}

and so $a = b$.
A similar proof would prove that if $a \neq 0$ and $ab = ac$, then $b = c$.
