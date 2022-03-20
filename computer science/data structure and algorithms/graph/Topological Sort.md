A **topological sort** is an ordering of vertices in an a directed acyclic graph, such that if there is a path from `v` to `u` , then `u`appears after `v` in the ordering.

### Indegree Sort
The indegree measures the number of incoming edges for a vertex. A vertex with 0 indegree will sorted in front of a vertex of 1 indegree. 

The general approach of the sorting is as follows
1. Compute the indegree for all vertices, this is straight forward with adjacency list
2. Use a queue to track the sequence, scan through the vertices, enqueue all vertices with indegree = 0
3. while this queue is not empty, **dequeue**
4. decrement all the indegree of the neighbors of the dequeued element
5. enqueue the neighbor if its indegree is 0
6. repeat until queue is empty, the topological order is the order of **dequeue**