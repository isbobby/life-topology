## Predicates
In logic, predicates can be obtained by removing some or all of the nouns in a statement. A predicate is a *predicate symbol* together with suitable *predicate variables*.

> [!Predicates]
> A **predicate** is a sentence that contains a finite number of variables and becomes a **statement** when values are substituted for the variables. The **domain** of a predicate variable is the set of all values that may be substituted in place of the variable.

For example, the sentence "Julius is the emperor of Rome" can have its nouns (Julius and Rome) replaced with *x* and *y*. "being an emperor of" can also be represented with a predicate symbol **Q**. With the predicate symbol and variables defined, the above sentence can be represented with $Q(x,y)$. The truth value of $Q(x,y)$ depends on the value of *x* and *y*.

> [!Truth Set]
> If $P(x)$ is a predicate and $x$ has domain $D$, the **truth set** is the set of all elements of $D$ that makes $P(x)$ true when they are substituted for $x$. The truth set of $P(x)$ is denoted ($x$ in $D$ given $P(x)$ is true) $$\{x \in D\ | P(x) \}$$

## Quantifiers
### Universal Quantifier $\forall$
> [!Definition]
> Let $Q(x)$ be a predicated and $D$ the domain of $x$. A **universal statement** is a statement of the form "$\forall x\ D, Q(x)$". It is defined true if, and only if, $Q(x)$ is true for every $x$ in $D$.
> 
> The statement is false, if and only if, $Q(x)$ is false for at least one $x$ in $D$. A value for $x$ for which $Q(x)$ is false is called a **counterexample** to the universal statement.

**Proving Universal Statements**
*Method of exhaustion*  can be used to prove the correctness of universal statement. It consists of showing the truth of the predicate separately for each individual element of the domain. This method can (in theory) be used whenever there is a finite domain.


### Existential Quantifier $\exists$
> [!Definition]
> Let $Q(x)$ be a predicate and $D$ the domain of x. An **existential statement** is a statement of the form $\exists x \in D, Q(x)$. It is defined to be true $Q(x)$ is true for at least one $x$ from $D$. It is false if, and only if, $Q(x)$ is false for all $x$ in $D$.

---
