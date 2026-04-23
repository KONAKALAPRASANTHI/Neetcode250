# 🧩 Valid Sudoku

## 📖 Problem Statement

You are given a `9 x 9` Sudoku board. Determine if the board is valid based on the following rules:

* Each row must contain digits `1-9` without duplicates
* Each column must contain digits `1-9` without duplicates
* Each `3 x 3` sub-box must contain digits `1-9` without duplicates

Return `true` if the board is valid, otherwise return `false`.

> ⚠️ Note: The board may be partially filled and does not need to be solvable.

---

## 🔍 Example

**Input:**

```id="k2v9qp"
board = [
["1","2",".",".","3",".",".",".","."],
["4",".",".","5",".",".",".",".","."],
[".","9","8",".",".",".",".",".","3"],
["5",".",".",".","6",".",".",".","4"],
[".",".",".","8",".","3",".",".","5"],
["7",".",".",".","2",".",".",".","6"],
[".",".",".",".",".",".","2",".","."],
[".",".",".","4","1","9",".",".","8"],
[".",".",".",".","8",".",".","7","9"]
]
```

**Output:**

```id="m7x4ld"
true
```

---

## 💡 Description

We use a **set to track seen elements**:

For each number, we create unique identifiers:

* `(num, row, i)` → checks row duplicates
* `(num, col, j)` → checks column duplicates
* `(num, box, i//3, j//3)` → checks 3×3 box duplicates

If any of these already exist in the set → invalid board.

---

## 🧾 Solution (Python)

```python id="z9p3xr"
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:

        seen = set()

        for i in range(9):
            for j in range(9):
                num = board[i][j]

                if num == ".":
                    continue

                row_key = (num, "row", i)
                col_key = (num, "col", j)
                box_key = (num, "box", i // 3, j // 3)

                if row_key in seen or col_key in seen or box_key in seen:
                    return False

                seen.add(row_key)
                seen.add(col_key)
                seen.add(box_key)

        return True
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(1) *(fixed 9×9 board)*
* **Space Complexity:** O(1)

---

## 🚀 Key Insight

By encoding row, column, and box constraints into a single set, we can efficiently detect duplicates in one pass.

---

## ⚠️ Edge Cases

* Empty cells (`"."`) should be ignored
* Duplicate in row, column, or box → invalid
* Board may be incomplete but still valid

---

## 🏷️ Tags

`Array` `HashSet` `Matrix`
