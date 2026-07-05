# Shortest Transformation Length in a Word List (Word Ladder 1)

## Problem Statement

Given two distinct words `s` (start) and `e` (end), and a list of unique words `words[]`, where all words have the same length, find the length of the **shortest transformation sequence** from `s` to `e`.

A valid transformation sequence must satisfy the following conditions:

- Only **one character** can be changed in each transformation.
- Every transformed word must exist in `words[]`, including `e`.
- All words contain only lowercase English letters.
- `s` may or may not be present in `words[]`.

Return the length of the shortest transformation sequence. If no valid transformation exists, return **0**.

---

## Example

### Input

```text
words[] = ["des", "der", "dfr", "dgt", "dfs"]
s = "der"
e = "dfs"
```

### Output

```text
3
```

### Explanation

```text
der → dfr → dfs
```

The transformation contains **3 words**, so the answer is **3**.

---

## Approach

This problem can be modeled as finding the **shortest path in an unweighted graph**.

### Key Observation

- Each word represents a **node**.
- An edge exists between two words if they differ by **exactly one character**.
- Since every transformation has the same cost (one step), **Breadth-First Search (BFS)** guarantees the shortest path.

### Algorithm

1. Store all dictionary words in a **HashSet** for fast lookup.
2. If the destination word is not present in the dictionary, return **0**.
3. Initialize a **Queue** for BFS.
4. Push the starting word with an initial transformation length of **1**.
5. While the queue is not empty:
   - Remove the front word.
   - If it matches the destination word, return the current length.
   - Generate all possible words by changing one character at every position.
   - If a generated word exists in the dictionary:
     - Push it into the queue with length + 1.
     - Remove it from the dictionary to prevent revisiting.
6. If BFS finishes without reaching the destination, return **0**.

---

## Why BFS?

- Every transformation has equal cost.
- BFS explores words level by level.
- The first time the destination is reached, it is guaranteed to be the shortest transformation.

---

## Time Complexity

- Let:
  - **N** = Number of words
  - **M** = Length of each word

For each word, we try:
- `M` positions
- `26` possible character replacements

**Time Complexity:** `O(N × M × 26)` ≈ **O(N × M)**

---

## Space Complexity

- HashSet for dictionary
- Queue for BFS

**Space Complexity:** `O(N)`

---

## Data Structures Used

- **HashSet** → Fast word lookup and removal (`O(1)`)
- **Queue** → Breadth-First Search traversal

---

## Intuition

Instead of comparing every word with every other word, we generate all possible one-letter transformations of the current word. Whenever a generated word exists in the dictionary, it becomes the next valid state in the BFS traversal.

Since BFS explores transformations level by level, the first occurrence of the destination word always represents the minimum number of transformations required.

---

## Tags

`Graph` `BFS` `Shortest Path` `HashSet` `Queue` `Word Ladder`