# 🔢 Two Sum

## 🧩 Problem Statement
<img width="1352" height="816" alt="image" src="https://github.com/user-attachments/assets/b368c6a8-63fb-4859-b548-1cd80caee51b" />
---

## ✅ Method 1: Brute Force

### 💡 Idea

Check all possible pairs.

### 💻 Code

```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        n = len(nums)
        for i in range(n):
            for j in range(i + 1, n):
                if nums[i] + nums[j] == target:
                    return [i, j]
```

### ⏱ Complexity

* Time: `O(n²)`
* Space: `O(1)`

---

## ✅ Method 2: HashMap (Optimal)

### 💡 Idea

Store elements in a hashmap and check for complement.

### 💻 Code

```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        seen = {}

        for i in range(len(nums)):
            needed = target - nums[i]

            if needed in seen:
                return [seen[needed], i]

            seen[nums[i]] = i
```

### ⏱ Complexity

* Time: `O(n)`
* Space: `O(n)`

---

## ✅ Method 3: Sorting + Two Pointers

### 💡 Idea

Sort the array and use two pointers to find the pair.

⚠️ Note: Original indices are lost after sorting, so we store them.

### 💻 Code

```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        arr = [(num, i) for i, num in enumerate(nums)]
        arr.sort()

        left = 0
        right = len(arr) - 1

        while left < right:
            curr_sum = arr[left][0] + arr[right][0]

            if curr_sum == target:
                return [arr[left][1], arr[right][1]]
            elif curr_sum < target:
                left += 1
            else:
                right -= 1
```

### ⏱ Complexity

* Time: `O(n log n)` (due to sorting)
* Space: `O(n)`

---

## 📊 Summary

| Method       | Approach          | Time       | Space |
| ------------ | ----------------- | ---------- | ----- |
| Brute Force  | Check all pairs   | O(n²)      | O(1)  |
| HashMap      | Store complements | O(n)       | O(n)  |
| Two Pointers | Sort + scan       | O(n log n) | O(n)  |

---

## 🔥 Final Takeaways

* Brute force is simple but inefficient
* HashMap is **best and most used in interviews**
* Two-pointer works only after sorting (with extra space for indices)

---
