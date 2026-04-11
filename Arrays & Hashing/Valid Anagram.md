## 🧩 Problem Statement
<img width="1598" height="694" alt="image" src="https://github.com/user-attachments/assets/a84f53a8-5937-4e73-9ae8-4c53a269c941" />

---

## ✅ Method 1: Sorting

### 💡 Idea

Sort both strings and compare them.

### 💻 Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return sorted(s) == sorted(t)
```

### ⏱ Complexity

* Time: `O(n log n)`
* Space: `O(n)`

---

## ✅ Method 2: Two HashMaps

### 💡 Idea

Count frequency of characters in both strings and compare.

### 💻 Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        countS = {}
        countT = {}

        for ch in s:
            countS[ch] = countS.get(ch, 0) + 1

        for ch in t:
            countT[ch] = countT.get(ch, 0) + 1

        return countS == countT
```

### ⏱ Complexity

* Time: `O(n)`
* Space: `O(n)`

---

## ✅ Method 3: Single HashMap

### 💡 Idea

Use one hashmap:

* Increase count for `s`
* Decrease count for `t`

### 💻 Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        count = {}

        for ch in s:
            count[ch] = count.get(ch, 0) + 1

        for ch in t:
            if ch not in count:
                return False
            count[ch] -= 1
            if count[ch] < 0:
                return False

        return True
```

### ⏱ Complexity

* Time: `O(n)`
* Space: `O(n)`

---

## ✅ Method 4: Array (Most Optimal)

### 💡 Idea

Use a fixed array of size 26 (for lowercase letters).

### 💻 Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False

        count = [0] * 26

        for i in range(len(s)):
            count[ord(s[i]) - ord('a')] += 1
            count[ord(t[i]) - ord('a')] -= 1

        for num in count:
            if num != 0:
                return False

        return True
```

### ⏱ Complexity

* Time: `O(n)`
* Space: `O(1)`

---

## 📊 Summary

| Method         | Approach               | Time       | Space |
| -------------- | ---------------------- | ---------- | ----- |
| Sorting        | Compare sorted strings | O(n log n) | O(n)  |
| Two HashMaps   | Count both             | O(n)       | O(n)  |
| Single HashMap | Increment & decrement  | O(n)       | O(n)  |
| Array          | Fixed size count       | O(n)       | O(1)  |

---

## 🔥 Final Takeaways

* Sorting is simple but slower
* HashMap is efficient and flexible
* Array method is **most optimal** (best for interviews)

---
