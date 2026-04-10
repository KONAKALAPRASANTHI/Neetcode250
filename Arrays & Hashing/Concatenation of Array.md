
# 🧩 1. Concatenation of Array

## 📌 Problem
![Question](https://github.com/user-attachments/assets/80f77f56-23ea-474b-bc38-154164c1f985)

---

## 💻 Code

### ✅ Method 1 (Optimal)
```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        return nums * 2
```
### ⏱ Complexity
- **Time:** O(n)
- **Space:** O(n)
---
### 🔁 Method 2 (Using `+`)
```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        return nums + nums
```
### ⏱ Complexity
- **Time:** O(n)
- **Space:** O(n)
---
### 🔁 Method 3 (Using Loop)
```python
class Solution:
    def getConcatenation(self, nums: List[int]) -> List[int]:
        ans = []
        for i in range(len(nums)):
            ans.append(nums[i])
        for i in range(len(nums)):
            ans.append(nums[i])
        return ans
```
### ⏱ Complexity
- **Time:** O(n)
- **Space:** O(n)
---

## ⚖️ Why Method 1 is Optimal?

Even though all methods have the same time and space complexity:

### ⏱ Complexity
- **Time:** O(n)
- **Space:** O(n)

Method 1 is considered optimal because:

- ✅ Uses Python’s built-in operation (`nums * 2`)
- ✅ Internally optimized (implemented in C)
- ✅ Avoids explicit loops
- ✅ More concise and readable

---

### 🚀 Comparison

| Method | Approach | Performance |
|-------|--------|------------|
| Method 1 | `nums * 2` | 🚀 Fastest |
| Method 2 | `nums + nums` | ⚡ Fast |
| Method 3 | Loop | 🐢 Slowest |

---

### 🎯 Conclusion
All methods are correct, but **Method 1 is preferred** because it is:
- Cleaner  
- Faster in practice  
- More Pythonic  
