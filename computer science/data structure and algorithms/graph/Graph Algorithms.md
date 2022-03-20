Graphs contain vertices and edges. They can be represented with *adjacency matrix* or *adjacency list*.

### Adjacency Matrix
Uses a 2D array `m[v][v]` to represent graph. An edge `(u,v)` is represented by setting `m[u][v] = true` or `m[u][v] = weight`. This is only efficient in representing dense graphs.

### Adjacency List
Uses an array of linked list to represent graph. An edge `(u,v)` is represented by appending `v` to `list[u]`. This is more efficient in representing sparse graphs.

### [[Topological Sort]]
A **topological sort** is an ordering of vertices in an a directed acyclic graph, such that if there is a path from `v` to `u` , then `u`appears after `v` in the ordering.

### [[Shortest-Path Algorithms]]
Given as input a weighted graph, and a distinguished vertex s, find the shortest weight path from s to every other vertex on G.

