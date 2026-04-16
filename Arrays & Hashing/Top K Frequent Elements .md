# 🧩 Top K Frequent Elements

## 📖 Problem Statement

Given an integer array `nums` and an integer `k`, return the `k` most frequent elements.

The test cases are generated such that the answer is always unique.
You may return the output in any order.

---

## 🔍 Example

**Input:**

```id="r8x1qp"
nums = [1,2,2,3,3,3], k = 2
```

**Output:**

```id="m2v9ld"
[2,3]
```

---

## 💡 Description

We solve this using **Bucket Sort**:

1. Count frequency of each element using a hashmap
2. Create buckets where index = frequency
3. Store elements in their respective frequency bucket
4. Traverse buckets from high to low frequency to get top `k` elements

This avoids sorting the entire array.

---

## 🧾 Solution (Python)

```python id="n5t7zw"
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        freq = {}
        
        for num in nums:
            if num in freq:
                freq[num] += 1
            else:
                freq[num] = 1

        bucket = [[] for _ in range(len(nums) + 1)]

        for num, f in freq.items():
            bucket[f].append(num)

        result = []

        for i in range(len(bucket) - 1, 0, -1):
            for num in bucket[i]:
                result.append(num)
                if len(result) == k:
                    return result
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(N)

---

## 🚀 Key Insight

Instead of sorting elements, we group them by frequency and directly pick the most frequent ones using bucket sort.

---

## ⚠️ Note

* More efficient than sorting (O(N log N))
* Works well when frequency range is limited

---

## 🏷️ Tags

`Array` `HashMap` `Bucket Sort` `Heap`
