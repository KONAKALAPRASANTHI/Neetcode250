# 🧩 2. Contains Duplicate

## 📌 Problem
![Question](https://github.com/user-attachments/assets/451b2189-ec15-4a8f-be0e-aab3f910899a?raw=true)

---

## 💻 Code

### ✅ Method 1 (Optimal - Using Set)
```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        seen = set()
        for num in nums:
            if num in seen:
                return True
            seen.add(num)
        return False
```
Time Complexity: O(n)
Space Complexity: O(n)
---

### 🔁 Method 2 (Using List)
```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        seen = []
        for num in nums:
            if num in seen:
                return True
            seen.append(num)
        return False
```
Time Complexity: O(n²) ❗
Space Complexity: O(n)
---

### 🔁 Method 3 (Sorting)
```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        nums.sort()
        for i in range(1, len(nums)):
            if nums[i] == nums[i - 1]:
                return True
        return False
```
Time Complexity: O(n log n)
Space Complexity: O(1)
---

### ❌ Method 4 (Brute Force - Fixed)
```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        n = len(nums)
        for i in range(n):
            for j in range(i + 1, n):
                if nums[i] == nums[j]:
                    return True
        return False
```
Time Complexity: O(n²)
Space Complexity: O(1)
---
---

## 📊 Comparison Table

| Method | Approach        | Time Complexity | Space Complexity | Notes |
|--------|---------------|----------------|------------------|------|
| ✅ Method 1 | Using Set      | O(n)           | O(n)             | Fastest lookup (O(1)), optimal solution |
| 🔁 Method 2 | Using List     | O(n²)          | O(n)             | Membership check is slow (O(n)) |
| 🔁 Method 3 | Sorting        | O(n log n)     | O(1)             | Modifies input array |
| ❌ Method 4 | Brute Force    | O(n²)          | O(1)             | Worst performance |

---
👉 **Best Choice:** Method 1 (Using Set) — optimal balance of time and simplicity.
