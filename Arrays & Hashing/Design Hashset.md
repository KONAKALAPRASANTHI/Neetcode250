# 🧩 Design HashSet

## 📖 Problem Statement

Design a HashSet without using any built-in hash table libraries.

Implement the `MyHashSet` class:

* `void add(key)` → Inserts the value `key` into the HashSet
* `bool contains(key)` → Returns whether the value `key` exists in the HashSet
* `void remove(key)` → Removes the value `key` from the HashSet

---

## 🔍 Example

**Input:**

```id="d9x3k1"
["MyHashSet", "add", "add", "contains", "contains", "add", "contains", "remove", "contains"]
[[], [1], [2], [1], [3], [2], [2], [2], [2]]
```

**Output:**

```id="wq7l2m"
[null, null, null, true, false, null, true, null, false]
```

---

## 💡 Description

We simulate a HashSet using a **boolean array**.

* The index represents the key
* The value at that index (`True/False`) represents whether the key exists

This works because the problem constraints allow keys in the range `[0, 10^6]`.

---

## 🧾 Solution (Python)

```python id="3g6p9k"
class MyHashSet:

    def __init__(self):
        self.data = [False] * 1000001
        
    def add(self, key: int) -> None:
        self.data[key] = True

    def remove(self, key: int) -> None:
        self.data[key] = False
        
    def contains(self, key: int) -> bool:
        return self.data[key]
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:**

  * add → O(1)
  * remove → O(1)
  * contains → O(1)

* **Space Complexity:** O(10⁶)

---

## 🚀 Key Insight

By directly mapping keys to indices, we achieve constant-time operations without needing hashing logic.

---

## ⚠️ Limitation

* Uses large memory (fixed size array)
* Works only when key range is limited

---

## 🏷️ Tags

`Array` `Hashing` `Design`
