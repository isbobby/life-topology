> [!principle of Mathematical Induction]
> Let $P(n)$ be a property that is defined for integer $n$, let $a$ be a fixed integer. Suppose the two following two statements are true
> 1. $P(a)$ is true
> 2. For all integers $k \geq a$, if $P(k)$ is true then $P(k+1)$ is true.
> 
> Then the statement for all integers $n \geq a$, $P(n)$ is true

The validity of proof by mathematical induction is generally taken as an axiom - that's why it is referred to as the *principle* of mathematical induction rather than as a theorem.

Proving by induction requires two steps - **basis step** and **inductive step**. The basis step needs to show $P(a)$ is true. The inductive step needs to show that for all integers, $k \geq a$, if $P(k)$ is true then $P(k + 1)$ is also true.

To perform the **inductive step**, first suppose $P(k)$ is true where $k$ is any particular but arbitrary integer larger than $a$ (this supposition is called the **inductive hypothesis**). Then show $P(k+1)$ to be true.

### Number Sequence Example
Mathematical induction can be used to prove $1 + 2 + 3 ... n = \frac{n(n+1)}{2}$ is true for all n.

**Basis Step**
Let $n = 1$, $P(1) = 1 = \frac{1+2}{2} = 1$, $P(1)$ is true

**Inductive Step**
Let $k \geq 1$  such that $1 + 2 + 3 ... k = \frac{k(k+1)}{2}$. Suppose $P(k+1)$ is true, we need to show $P(k+1)$ is also true.

For $k+1$, $1 + 2 + 3 ... k+1 = \frac{(k+1)(k+2)}{2}$, $1 + 2 + 3 ... k + k+1 = \frac{(k+1)(k+2)}{2}$. 

The LHS can be substituted with the result from the inductive hypothesis, where $\frac{k(k+1)}{2} + k+1 = \frac{(k+1)(k+2)}{2}$. This equation is true based on algebra manipulation.

Therefore, $P(k+1)$ is also true. Since we have proved both the basis step and the inductive step, we conclude the theorem is true by induction.

## 
The main tool used to prove the correctness of a mathematical sequence is mathematical induction. Mathematical induction is a three step process.

First, the base case is proven, denoted as $P(1)$. This acts like the first piece of domino which sets the foundation of what's going to happen.

Second, a inductive hypothesis is generated where *k-th* case $P(k)$ is assumed to be true.

The last step is the proving step where the *k+1* case $P(k+1)$ has to be proven base on the previously generated inductive hypothesis. A common way of doing it is to substitute the result from $P(k)$ in to the equation of $P(k+1)$.
