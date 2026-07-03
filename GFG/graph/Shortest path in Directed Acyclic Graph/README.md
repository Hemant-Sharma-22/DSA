# Shortest Path in Directed Acyclic Graph (DAG)

## Problem Statement

Given a **Directed Acyclic Graph (DAG)** with `V` vertices numbered from `0` to `V-1` and a list of directed weighted edges, find the shortest distance from the source vertex `0` to every other vertex.

If a vertex is not reachable from the source, return `-1` for that vertex.

---

## Example

### Input

```text
V = 6
E = 7

Edges:
0 -> 1 (2)
0 -> 4 (1)
4 -> 5 (4)
4 -> 2 (2)
1 -> 2 (3)
2 -> 3 (6)
5 -> 3 (1)
```

### Output

```text
[0, 2, 3, 6, 1, 5]
```

### Explanation

* Distance to `0` = `0`
* Distance to `1` = `2`
* Distance to `2` = `3` via `0 → 4 → 2`
* Distance to `3` = `6` via `0 → 4 → 5 → 3`
* Distance to `4` = `1`
* Distance to `5` = `5`

---

## Approach

Since the graph is a **Directed Acyclic Graph (DAG)**, we first compute a **Topological Ordering** of all vertices.

After obtaining the topological order:

1. Initialize all distances as **Infinity**.
2. Set the source vertex (`0`) distance to `0`.
3. Process each vertex in topological order.
4. Relax all outgoing edges.
5. Replace unreachable vertices with `-1`.

This approach guarantees that every vertex is processed only after all of its predecessors.

---

## Algorithm

1. Build the adjacency list.
2. Perform Topological Sort using DFS.
3. Initialize the distance array.
4. Traverse vertices in topological order.
5. Relax every outgoing edge.
6. Convert unreachable distances to `-1`.
7. Return the distance array.

---

## Complexity Analysis

* **Time Complexity:** `O(V + E)`
* **Space Complexity:** `O(V + E)`

---

## Key Concepts

* Directed Acyclic Graph (DAG)
* Topological Sort
* DFS
* Shortest Path
* Edge Relaxation
* Graph Traversal

---

## Tags

`Graph` `DFS` `Topological Sort` `Shortest Path` `DAG`
