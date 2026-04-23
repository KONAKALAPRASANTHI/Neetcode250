# 🧩 Range Sum Query 2D – Immutable

## 📖 Problem Statement

You are given a 2D matrix `matrix`. Handle multiple queries to calculate the sum of elements inside a rectangle defined by:

* Top-left corner → `(row1, col1)`
* Bottom-right corner → `(row2, col2)`

You must design an algorithm where `sumRegion` works in **O(1)** time.

---

## 🔍 Example

**Input:**

```id="k8z4qp"
matrix = [
 [3,0,1,4,2],
 [5,6,3,2,1],
 [1,2,0,1,5],
 [4,1,0,1,7],
 [1,0,3,0,5]
]

Queries:
sumRegion(2,1,4,3) → 8
sumRegion(1,1,2,2) → 11
sumRegion(1,2,2,4) → 12
```

---

## 💡 Description

We use a **2D Prefix Sum (Cumulative Sum)** approach:

* Precompute a matrix `p` where each cell stores sum from `(0,0)` to `(i,j)`
* This allows answering each query in constant time

### Formula:

To get sum of a rectangle:

```
sum = p[row2][col2]
    - p[row1-1][col2]
    - p[row2][col1-1]
    + p[row1-1][col1-1]
```

---

## 🧾 Solution (Python)

```python id="m4x9zt"
class NumMatrix:

    def __init__(self, matrix: List[List[int]]):
        rows = len(matrix)
        cols = len(matrix[0])
        self.p = [[0] * cols for _ in range(rows)]

        for i in range(rows):
            for j in range(cols):
                self.p[i][j] = matrix[i][j]
                
                if i > 0:
                    self.p[i][j] += self.p[i-1][j]   # top
                if j > 0:
                    self.p[i][j] += self.p[i][j-1]   # left
                if i > 0 and j > 0:
                    self.p[i][j] -= self.p[i-1][j-1] # overlap

    def sumRegion(self, row1: int, col1: int, row2: int, col2: int) -> int:
        res = self.p[row2][col2]

        if row1 > 0:
            res -= self.p[row1-1][col2]
        if col1 > 0:
            res -= self.p[row2][col1-1]
        if row1 > 0 and col1 > 0:
            res += self.p[row1-1][col1-1]

        return res
```

---

## ⏱️ Complexity Analysis

* **Preprocessing Time:** O(M × N)
* **Query Time:** O(1)
* **Space Complexity:** O(M × N)

---

## 🚀 Key Insight

Precompute prefix sums once, so each query can be answered instantly using inclusion-exclusion.

---

## ⚠️ Note

* This is an **immutable matrix** (no updates)
* For mutable matrices, a different approach (Fenwick Tree / Segment Tree) is needed

---

## 🏷️ Tags

`Array` `Matrix` `Prefix Sum`
