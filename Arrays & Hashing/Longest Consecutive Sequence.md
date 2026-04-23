# 🧩 Longest Consecutive Sequence

## 📖 Problem Statement

Given an array of integers `nums`, return the length of the **longest consecutive sequence**.

A consecutive sequence is one where each element is exactly `1` greater than the previous element.
The elements do not need to be adjacent in the original array.

You must write an algorithm that runs in **O(n)** time.

---

## 🔍 Example

**Input:**

```id="p6x3lm"
nums = [2,20,4,10,3,4,5]
```

**Output:**

```id="r8z1qt"
4
```

**Explanation:**
The longest consecutive sequence is `[2, 3, 4, 5]`.

---

## 💡 Description

We use a **HashSet** for efficient lookups:

1. Convert the array into a set
2. Only start counting when the number is the **start of a sequence**

   * i.e., `n - 1` is not in the set
3. Expand forward (`n + 1, n + 2, ...`) to count sequence length
4. Track the maximum length

This avoids unnecessary repeated work and ensures O(n) time.

---

## 🧾 Solution (Python)

```python id="t9k2vr"
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        num_set = set(nums)
        longest = 0

        for n in num_set:
            if n - 1 not in num_set:
                length = 1

                while n + length in num_set:
                    length += 1

                longest = max(longest, length)

        return longest
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(N)

---

## 🚀 Key Insight

Only start counting from numbers that are **sequence starters** (no previous number), which avoids redundant checks.

---

## ⚠️ Edge Cases

* Empty array → return 0
* Duplicate elements → handled using set
* Single element → return 1

---

## 🏷️ Tags

`Array` `HashSet`
