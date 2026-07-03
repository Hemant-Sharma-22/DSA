# Alien Dictionary

## Problem Statement

A new alien language uses the English alphabet, but the order of its letters is unknown. You are given a list of words sorted lexicographically according to the alien language.

Determine a valid ordering of the unique characters. If multiple valid orderings exist, return any one of them.

If the given dictionary is inconsistent and no valid ordering exists, return an empty string.

---

## Example

### Input

```text
words = ["baa", "abcd", "abca", "cab", "cad"]
```

### Output

```text
"bdac"
```

### Explanation

* `b` comes before `a`
* `d` comes before `a`
* `a` comes before `c`
* `b` comes before `d`

One valid character ordering is:

```text
b → d → a → c
```

---

## Approach

Treat each unique character as a node in a directed graph.

By comparing every pair of adjacent words, find the first differing character. This difference establishes a directed edge indicating the order between the two characters.

Once the graph is constructed:

1. Compute the indegree of every character.
2. Perform **Topological Sorting (Kahn's Algorithm)**.
3. Build the character ordering while processing nodes with zero indegree.
4. If all characters are processed, return the ordering.
5. Otherwise, a cycle exists, so return an empty string.

---

## Algorithm

1. Create a graph containing all unique characters.
2. Compare each pair of adjacent words.
3. Add a directed edge from the first differing character of the first word to that of the second word.
4. Calculate the indegree of every character.
5. Apply Topological Sort using a queue.
6. If the resulting ordering contains all unique characters, return it.
7. Otherwise, return an empty string.

---

## Complexity Analysis

* **Time Complexity:** `O(N × L + K)`

  * `N` = Number of words
  * `L` = Average length of a word
  * `K` = Number of unique characters
* **Space Complexity:** `O(K + E)`

  * `E` = Number of precedence relationships (edges)

---

## Key Concepts

* Graph
* Directed Graph
* Topological Sort
* Kahn's Algorithm
* BFS
* Indegree
* Lexicographical Ordering

---

## Tags

`Graph` `Topological Sort` `BFS` `Kahn's Algorithm` `Directed Graph`
