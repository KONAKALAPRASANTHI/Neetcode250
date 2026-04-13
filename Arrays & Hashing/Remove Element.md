# 🧩 Remove Element

## 📖 Problem Statement

You are given an integer array `nums` and an integer `val`. Your task is to remove all occurrences of `val` from `nums` **in-place**.

After removing all occurrences, return the number of remaining elements `k`, such that the first `k` elements of `nums` do not contain `val`.

### ⚠️ Note

* Order of elements does not matter
* Ignore elements beyond the first `k` positions
* Modify the array in-place

---

## 🔍 Example

**Input:**

```
nums = [1,1,2,3,4], val = 1
```

**Output:**

```
k = 3
nums = [2,3,4,_,_]
```

---

## 💡 Description

We use a **two-pointer approach**:

* One pointer `i` scans the array
* Another pointer `k` keeps track of the position to place valid elements

Whenever we find an element not equal to `val`, we place it at index `k` and increment `k`.

---

## 🧾 Solution (Python)

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        k = 0

        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1

        return k
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(1)

---

## 🚀 Key Insight

Use a **slow pointer (`k`)** to overwrite unwanted elements while traversing the array with a fast pointer.

---

## 🏷️ Tags

`Array` `Two Pointers`
