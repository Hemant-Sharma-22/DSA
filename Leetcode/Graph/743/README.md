# 743. Network Delay Time (pure Dijkshtra's Algo)

## Problem Statement

You are given a directed, weighted graph consisting of `n` nodes labeled from `1` to `n`.

Each edge is represented as:

```text
times[i] = [u, v, w]
```

where:

- `u` → Source node
- `v` → Destination node
- `w` → Time taken for the signal to travel from `u` to `v`

A signal is sent from a starting node `k`.

Return the **minimum time required for all nodes to receive the signal**.

If at least one node cannot be reached, return **-1**.

---

## Example

### Input

```text
times = [[2,1,1],[2,3,1],[3,4,1]]
n = 4
k = 2
```

### Output

```text
2
```

### Explanation

```text
2 → 1 (1)

2 → 3 (1)

2 → 3 → 4 (2)
```

The last node receives the signal after **2 units of time**.

---

## Intuition

The signal starts from a single source and spreads through the network.

We need to determine the **minimum time** required for the signal to reach every node.

Since every edge has a **non-negative weight**, this becomes a **Single Source Shortest Path** problem, making **Dijkstra's Algorithm** the ideal choice.

Once the shortest distance from the source to every node is known:

- If any node is unreachable, return **-1**.
- Otherwise, the answer is the **maximum** shortest distance among all nodes.

---

## Approach

### Step 1: Build the Graph

Create an adjacency list where every node stores:

```text
(neighbor, weight)
```

Since the graph is **directed**, only add:

```text
u → v
```

Do **not** add the reverse edge.

---

### Step 2: Initialize Dijkstra

- Distance array initialized to Infinity.
- Distance of source node = 0.
- Push `(distance, node)` into a Min Heap (Priority Queue).

---

### Step 3: Process Nodes

While the priority queue is not empty:

- Remove the node having the smallest distance.
- Skip outdated entries.
- Relax all outgoing edges.
- Update the distance whenever a shorter path is found.

---

### Step 4: Compute the Answer

After Dijkstra finishes:

- If any node still has distance = Infinity, return **-1**.
- Otherwise, return the **maximum value** in the distance array.

---

## Why Dijkstra?

- All edge weights are **non-negative**.
- We need the shortest distance from one source to all other nodes.
- Dijkstra guarantees the optimal shortest paths efficiently.

---

## Time Complexity

Let:

- **V** = Number of nodes
- **E** = Number of edges

Building the graph:

```text
O(E)
```

Dijkstra:

```text
O((V + E) log V)
```

Overall:

```text
O((V + E) log V)
```

---

## Space Complexity

Adjacency List:

```text
O(V + E)
```

Distance Array:

```text
O(V)
```

Priority Queue:

```text
O(V)
```

Overall:

```text
O(V + E)
```

---

## Data Structures Used

- **Adjacency List** → Store the directed weighted graph.
- **Priority Queue (Min Heap)** → Always process the node with the smallest current distance.
- **Distance Array** → Stores the shortest known distance from the source to every node.

---

## Key Observations

- The graph is **directed**.
- Edge weights are **non-negative**, so Dijkstra is applicable.
- The answer is **not** the sum of distances.
- The answer is the **largest shortest distance**, since all nodes receive the signal simultaneously through their shortest paths.
- If even one node cannot be reached, the result is **-1**.

---

## Tags

`Graph` `Shortest Path` `Dijkstra` `Priority Queue` `Heap` `Adjacency List`