> [! Definition]
> An **argument** is a sequence of statements, and an **argument form** is a sequence of statement forms. All statements in an argument except the last one are premises, the final statement is the **conclusion**.
> 
> An argument is valid means that no matter what particular statements are substituted for the statement variables in its premises, the resulting premises are all true, then the conclusion is also true.
> 
> An argument is invalid when all its premises are true, and its conclusion false. Therefore, to verify the validity, check that conclusion is true for **all** cases where premises are true.

## Argument Form Patterns
### *Modus Ponens* - Method of affirming
1. If $p$ then $q$
2. $p$
3. $\therefore q$

This form of argument uses the conclusion as an affirmation. For example,

1. If 12 is divisible by 6, then it is divisible by 3
2. 12 is divisible by 6
3. Therefore, 12 is divisible by 6

---
### *Modus Tollens* - Method of denial
1. If $p$ then $q$
2. $\neg\ q$
3. $\therefore \neg\ p$

This form of argument uses the conclusion as denial, for example

1. If Zeus is human, he is mortal
2. Zeus is immortal
3. Therefore Zeus is non-human

---
### Specification
Both argument forms below are valid
- $p \land q$ $\therefore p$
- $p \land q$ $\therefore q$

### Elimination
1. $p \lor q$ 
2. $\neg \ q$
3. $\therefore p$

### Transitivity
1. $p \to q$ 
2. $q \to r$ 
3. $\therefore p \to r$

### Division into Cases
1.  $p \lor q$
2.  $p \to r$
3. $q \to r$
4. $\therefore r$

If we are able to show in either case $p$ and $q$ a certain conclusion $r$ follows, then this conclusion must also be true

## Fallacies
A **fallacy** is an error in reasoning that results in an invalid argument. There common fallacies are **using ambiguous premises**, **circular reasoning** and **jumping to conclusions**.

For an argument to be valid, every argument of the same form whose premises are true must have a true conclusion. It follows that an invalid argument has form whose premises are all true but the conclusion is false.

### Converse Error
An converse error happens when the consequent is used to justify the truth of hypothesis. It has the following form

1. $p \to q$
2. $q$
3. $\therefore p$

### Inverse Error
The conclusion of this argument would have been valid if the premise $p \to q$ is replaced by its inverse. In [[Conditional Statements]], we have established the **consequent** remains vacuously true even if the **hypothesis is false**.

1. $p \to q$
2. $\neg\ p$
3. $\therefore \neg\ q$

### Valid Argument with a False Premise
Some argument can be valid, however, some of its premises, as well as its conclusion, can be wrong.

### Invalid Arguments with True Premises and True Conclusion
Some argument can also have true premises and true conclusion, this however, does not make them valid.

## Soundness of Argument
> [! Definition]
> An argument can be called sound if, and only if, it is valid and all its premises are true. An argument that is not sound is called unsound.

The bottom line of understanding and crafting argument, is that we can only be sure that the conclusion of an argument is true when we know that the argument is sound, that is, when we know both the argument is valid and all it has all true premises.

## Contradiction Rule
The following argument form using a contradiction is valid.
1. $\neg\ p \to c$  : if the negation of $p$ leads to a contradiction
2. $\therefore p$ : $p$ must be true

If an assumption leads to a contradiction, then the assumption must be false.
