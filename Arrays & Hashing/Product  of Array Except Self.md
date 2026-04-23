# 🧩 Product of Array Except Self

## 📖 Problem Statement

Given an integer array `nums`, return an array `output` such that:

* `output[i]` is equal to the product of all elements of `nums` except `nums[i]`
* Solve it in **O(n)** time
* Do **not use division**

---

## 🔍 Example

**Input:**

```id="q7x2mp"
nums = [1,2,4,6]
```

**Output:**

```id="k9z4tw"
[48,24,12,8]
```

---

## 💡 Description

We use a **prefix and suffix product approach**:

1. First pass → store product of all elements to the **left** of each index
2. Second pass → multiply with product of all elements to the **right**

This avoids using division and keeps space optimized.

---

## 🧾 Solution (Python)

```python id="p3n8vr"
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        n = len(nums)
        result = [1] * n

        # Left products
        for i in range(1, n):
            result[i] = result[i-1] * nums[i-1]

        # Right products
        right = 1
        for i in range(n-1, -1, -1):
            result[i] *= right
            right *= nums[i]

        return result
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(1) *(excluding output array)*

---

## 🚀 Key Insight

Each index result = product of **left elements × right elements**, computed efficiently in two passes.

---

## ⚠️ Edge Cases

* Array contains zero(s)
* Single element array
* Large values (handled by constraints)

---

## 🏷️ Tags

`Array` `Prefix Sum`
