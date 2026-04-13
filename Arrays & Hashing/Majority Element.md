# 🧩 Majority Element

## 📖 Problem Statement

Given an array `nums` of size `n`, return the **majority element**.

The majority element is the element that appears more than ⌊n / 2⌋ times in the array.
You may assume that the majority element always exists in the array.

---

## 🔍 Example

**Input:**

```
nums = [5,5,1,1,1,5,5]
```

**Output:**

```
5
```

---

## 💡 Description

This problem is solved using the **Boyer-Moore Voting Algorithm**.

* We maintain a `candidate` and a `count`.
* If count becomes 0, we choose a new candidate.
* If the current number equals the candidate → increment count.
* Otherwise → decrement count.

Since the majority element appears more than `n/2` times, it will always remain as the final candidate.

---

## 🧾 Solution (Python)

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        candidate = None

        for num in nums:
            if count == 0:
                candidate = num
            if candidate == num:
                count += 1
            else:
                count -= 1

        return candidate
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(1)

---

## 🚀 Key Insight

The majority element dominates the array, so even after cancellations with other elements, it remains as the final candidate.

---

## 🏷️ Tags

`Array` `Greedy`
