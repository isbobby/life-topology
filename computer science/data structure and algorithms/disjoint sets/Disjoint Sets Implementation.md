# Data Structure for Disjoint Sets
##### See [Github](https://github.com/isbobby/cs-fundamentals/tree/main/dsa/disjoint_sets) for implementation
## Requirements
Based on the problem requirement, we do not need a `find` operation which returns any specific name, just that `find` on two elements return the same answer if and only if they are in the same set.

One idea is to use a tree to represent each set, and the root of the tree will be the name of the set. The only information we need in this tree is the *parent link*. Since only the name of the parent is required, we can assume this tree is stored implicitly in an array similar to [[Binary Heaps]].

### Union
To perform a **union** of two sets, we merge the two trees by making the parent link of one tree's root link to the root node of the other tree. This operation takes constant time.

### Find
A `find(x)` on element **x**  is performed by returning the root of the tree containing **x**.  The time to perform this operation is proportional to the depth of the node representing **x**, assuming that we can find the node in constant time.

With the above strategy, we can create a tree of depth $N-1$ so the worst case running time for `find(x)` is $O(N)$.

## Better Unions

