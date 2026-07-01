````markdown
# Alien Dictionary

## Problem Description

A new alien language uses the English alphabet, but the order of letters is unknown. You are given a list of words `words[]` from the alien language's dictionary, where the words are sorted lexicographically according to the alien language.

Your task is to determine a valid order of the unique letters in this language. If multiple valid orders exist, return any one of them.

If the given dictionary is inconsistent and no valid ordering exists, return an empty string (`""`).

> **Note:** The returned order is validated by the driver code. Any correct ordering is accepted.

---

## Examples

### Example 1

**Input**

```text
words[] = ["baa", "abcd", "abca", "cab", "cad"]
```

**Output**

```text
"bdac"
```

**Explanation**

- `"baa"` → `"abcd"` ⇒ `b` comes before `a`
- `"abcd"` → `"abca"` ⇒ `d` comes before `a`
- `"abca"` → `"cab"` ⇒ `a` comes before `c`
- `"cab"` → `"cad"` ⇒ `b` comes before `d`

One valid ordering is:

```text
b → d → a → c
```

---

### Example 2

**Input**

```text
words[] = ["caa", "aaa", "aab"]
```

**Output**

```text
"cab"
```

**Explanation**

- `"caa"` → `"aaa"` ⇒ `c` comes before `a`
- `"aaa"` → `"aab"` ⇒ `a` comes before `b`

One valid ordering is:

```text
c → a → b
```

---

### Example 3

**Input**

```text
words[] = ["ab", "cd", "ef", "ad"]
```

**Output**

```text
""
```

**Explanation**

No valid ordering exists because the inferred character relationships create a contradiction.

---

## Constraints

- `1 ≤ words.length ≤ 500`
- `1 ≤ words[i].length ≤ 100`
- `words[i]` consists only of lowercase English letters.
````
