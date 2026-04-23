# 🧩 Sort Colors

## 📖 Problem Statement

You are given an array `nums` where:

* `0` represents red
* `1` represents white
* `2` represents blue

Sort the array **in-place** so that elements are grouped as:
`0 → 1 → 2`

You must not use any built-in sorting functions.

---

## 🔍 Example

**Input:**

```id="p4z8mx"
nums = [1,0,1,2]
```

**Output:**

```id="x9q2ld"
[0,1,1,2]
```

---

## 💡 Description

We use the **Dutch National Flag Algorithm** (three-pointer approach):

* `start` → position for next `0`
* `mid` → current element
* `end` → position for next `2`

### Logic:

* If `nums[mid] == 0` → swap with `start`, move both pointers
* If `nums[mid] == 1` → move `mid`
* If `nums[mid] == 2` → swap with `end`, move `end`

---

## 🧾 Solution (Python)

```python id="c8w3yt"
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        start = 0
        mid = 0
        end = len(nums) - 1
        
        while mid <= end:
            if nums[mid] == 0:
                nums[start], nums[mid] = nums[mid], nums[start]
                start += 1
                mid += 1
            elif nums[mid] == 1:
                mid += 1
            else:
                nums[mid], nums[end] = nums[end], nums[mid]
                end -= 1
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(1)

---

## 🚀 Key Insight

By maintaining three regions (0s, 1s, 2s), we can sort the array in a single pass without extra space.

---

## ⚠️ Note

* This is an **in-place algorithm**
* Very common interview question

---

## 🏷️ Tags

`Array` `Two Pointers` `Sorting`
