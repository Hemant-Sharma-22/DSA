# All Ancestors of a Node in a Directed Acyclic Graph

## Problem Statement

You are given a **Directed Acyclic Graph (DAG)** with `n` nodes numbered from `0` to `n - 1` and a list of directed edges.

For every node, find all of its **ancestors**. A node `u` is considered an ancestor of node `v` if there exists a directed path from `u` to `v`.

Return a list where `answer[i]` contains all ancestors of node `i` in **ascending order**.

---

## Example

### Input

```text
n = 8

edges = [
    [0,3],[0,4],[1,3],[2,4],
    [2,7],[3,5],[3,6],[3,7],[4,6]
]
```

### Output

```text
[
    [],
    [],
    [],
    [0,1],
    [0,2],
    [0,1,3],
    [0,1,2,3,4],
    [0,1,2,3]
]
```

### Explanation

* Nodes `0`, `1`, and `2` have no ancestors.
* Node `3` is reachable from `0` and `1`.
* Node `4` is reachable from `0` and `2`.
* Node `5` is reachable through node `3`, so its ancestors are `0`, `1`, and `3`.
* Node `6` inherits ancestors from both nodes `3` and `4`.
* Node `7` inherits ancestors from node `3` along with node `2`.

---

## Approach

Since the graph is a **Directed Acyclic Graph (DAG)**, first compute a **Topological Ordering** of all nodes.

While processing nodes in topological order:

1. Every node is an ancestor of its direct neighbors.
2. All ancestors of the current node are also ancestors of its neighbors.
3. Propagate ancestor information to each outgoing neighbor.
4. Store ancestors in a sorted data structure to maintain ascending order.

---

## Algorithm

1. Build the adjacency list.
2. Perform Topological Sort using DFS (or Kahn's Algorithm).
3. Initialize an ancestor set for every node.
4. Traverse nodes in topological order.
5. For every edge `u → v`:

   * Add `u` to the ancestor set of `v`.
   * Add all ancestors of `u` to the ancestor set of `v`.
6. Convert the ancestor sets into sorted lists.
7. Return the final answer.

---

## Complexity Analysis

* **Time Complexity:** `O((V + E) + E × A)`

  * `V` = Number of nodes
  * `E` = Number of edges
  * `A` = Average number of ancestors propagated
* **Space Complexity:** `O(V + E + V²)` (worst case)

---

## Key Concepts

* Directed Acyclic Graph (DAG)
* Graph Traversal
* Topological Sort
* DFS
* Ancestor Propagation
* Set Data Structure

---

## Tags

`Graph` `DAG` `DFS` `Topological Sort` `Graph Traversal`
