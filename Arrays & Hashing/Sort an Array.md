# 🧩 Sort an Array

## 📖 Problem Statement

Given an array of integers `nums`, sort the array in ascending order and return it.

You must solve the problem **without using built-in functions** and achieve **O(n log n)** time complexity with minimal space usage.

---

## 🔍 Example

**Input:**

```id="k3v8qp"
nums = [10,9,1,1,1,2,3,1]
```

**Output:**

```id="p7x2zs"
[1,1,1,1,2,3,9,10]
```

---

## 💡 Description

We use the **Merge Sort algorithm**, which follows the **divide and conquer** approach:

1. Divide the array into two halves
2. Recursively sort both halves
3. Merge the sorted halves

Merge Sort guarantees **O(n log n)** time complexity.

---

## 🧾 Solution (Python)

```python id="v4nq9m"
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        
        def merge_sort(nums):
            if len(nums) <= 1:
                return nums
            
            mid = len(nums) // 2
            left_half = nums[:mid]
            right_half = nums[mid:]
            
            left_half = merge_sort(left_half)
            right_half = merge_sort(right_half)
            
            return merge_arr(left_half, right_half)
        
        def merge_arr(left, right):
            result = []
            i, j = 0, 0
            
            while i < len(left) and j < len(right):
                if left[i] <= right[j]:
                    result.append(left[i])
                    i += 1
                else:
                    result.append(right[j])
                    j += 1
            
            result.extend(left[i:])
            result.extend(right[j:])
            
            return result
        
        return merge_sort(nums)
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N log N)
* **Space Complexity:** O(N)

---

## 🚀 Key Insight

Merge Sort divides the array until single elements remain and then merges them in sorted order, ensuring efficient sorting.

---

## ⚠️ Note

* This implementation uses extra space for merging
* In-place sorting with O(1) space is possible using **Heap Sort**, but it's more complex

---

## 🏷️ Tags

`Divide and Conquer` `Sorting` `Merge Sort`
