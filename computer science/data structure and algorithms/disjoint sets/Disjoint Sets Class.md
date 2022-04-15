# Disjoint Sets
## Equivalence Relations
#### SEE [[Discrete Math]] : [[Relations]]
A **relation** R is defined on a set S if for every pair of elements $a,b \in S, a\ R\ b$. $a\ R\ b$ is either true or false. If the $a\ R\ b$ is true, then we say a is related to b.

An equivalence relation must satisfy the three properties
1. *Reflexive* - $a\ R\ a$, for all $a \in S$

2. *Symmetric* - $a\ R\ b$, if and only if $b\ R\ a$

3. *Transitive* - $a\ R\ b$ and $b\ R\ c$ implies $a\ R\ c$

### $\geq$ is not an equivalent relation
$\geq$ is reflexive ($a \geq a$ for all $a$), and transitive (if $a \geq b, b \geq c, a \geq c$). It is however not symmetric - $a \geq b$ does not imply $b \geq a$.

### Electrical Connectivity
Electrical connectivity is a equivalent relation. Since every element is connected to itself (reflexivity), symmetric (two connected elements) and transitive.

## The Dynamic Equivalence Problem
Given an equivalence relation $\sim$, the problem is to decide, for any $a$ and $b$, if $a\ \sim b$.  If the relation is stored as a 2D array of boolean variables, this can be done in constant time. However, the relation is usually implicitly defined.

---
##### Example of Implicit Definition
Suppose the equivalence relation is defined over the five-element set `{a1, a2, a3, a4, a5}`. Then there are 25 pairs of elements, each of which is either related or not. However, the information $a1\ \sim a2$, $a3\ \sim a4$, $a5\ \sim a1$, $a2\ \sim a4$  implies all pairs are related (equivalence relation).

---

The **equivalence class** of an element $a \in S$ is the subset of $S$ that contains all the elements that are related to $a$. The equivalence class form a partition of $S$. Every member of $S$ appears in exactly one equivalence class. To decide if $a \sim b$, we only need to decide if $a,b$ are both in the same equivalence class.

The input is initially a collection of $N$ sets - this is because we assume that all relations (except reflexive to itself) are false. each set has a different element so that $S_i \cap\ S_j = \emptyset$; this makes the sets **disjoint**.

There are two permissible operations `find` and `union`. `find` returns the name of the set (the *equivalence class*) containing a given element. `union` adds relation.

To perform `union`, we first need to see if $a \sim b$. This is done by performing `find`  on both elements and see if they are in the same equivalence class. If they are not, we apply `union`. The `union` process merges the two equivalence class containing $a,b$ into a new equivalence class.

From a set perspective - the result of union is to create a new set $S_k = S_i\ \cup S_j$, which destroys the original and preserving the disjointness of all the sets. The algorithm to do this is frequently known as the disjoint set **union/find algorithm**.

---
##### Dynamic Nature of the Algorithm
The algorithm is *dynamic* because during the course of the *algorithm*, the sets can change via the **union** operation. The algorithm must also operate **online** - when a find is performed, it does not know the data it will be executing on beforehand.

In contrast, an **offline** algorithm will be allowed to see the entire sequence of **unions** and **finds**. The answer it provides for each **find** must still be consistent with all the **unions** that were performed up until the **find**.

---
In this algorithm, we do not perform any operations comparing the relative values of elements but merely require the knowledge of their location.

Secondly, the name of the set returned by **find** is actually arbitrary. All that really matters is `find(a) == find(b) -> true` if both elements are in the same set.

### Strategies to solve the problem
**1 - Constant time `find`**
We could maintain the name of each equivalent class in an array. The `find` operation will be a $O(1)$ look up. However, the `union` operation would require a linear scan to check if two elements are in the same equivalence class. A sequence of $N - 1$ `union` would therefore have $O(N^2)$ complexity.

**2 - Constant time `Union`**
The second approach is to keep the elements that are in the same equivalence class in a linked list. This saves time when updating because we do not have to search through the entire array when updating.

If we also *keep track of the size of each equivalence class*, and when performing **unions** we change the name of the smaller equivalence class to the larger, then the total time spent for $N - 1$ merges is $O(N log N)$.

## [[Disjoint Sets Implementation]]
