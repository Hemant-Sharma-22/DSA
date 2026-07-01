````markdown
# Bipartite Graph

## Problem Description

Given an undirected graph with `V` vertices represented by an adjacency list `edges`, determine whether the graph is **bipartite**.

A graph is bipartite if the vertices can be divided into two disjoint sets such that every edge connects a vertex from one set to a vertex in the other. In other words, no two adjacent vertices should belong to the same set.

Return `true` if the graph is bipartite; otherwise, return `false`.

---

## Example

### Input

```text
V = 4

edges = [
  [1,2],
  [0,2],
  [0,1,3],
  [2]
]
````

### Output

```text
false
```

### Explanation

Vertices `0`, `1`, and `2` form an odd cycle, making it impossible to divide the graph into two valid sets. Therefore, the graph is **not bipartite**.

---

## Constraints

* `1 <= V <= 100`
* `0 <= edges[i].length < V`
* `0 <= edges[i][j] < V`
* The graph is undirected.
* There are no self-loops.
* There are no duplicate edges.

```
```
