# 🧩 Design HashMap

## 📖 Problem Statement

Design a HashMap without using any built-in hash table libraries.

Implement the `MyHashMap` class:

* `MyHashMap()` → Initializes the object with an empty map
* `void put(key, value)` → Inserts a (key, value) pair into the HashMap. If the key already exists, update the value
* `int get(key)` → Returns the value mapped to the key, or `-1` if not found
* `void remove(key)` → Removes the key and its corresponding value

---

## 🔍 Example

**Input:**

```id="z2p9mk"
["MyHashMap", "put", "put", "get", "get", "put", "get", "remove", "get"]
[[], [1,1], [2,2], [1], [3], [2,1], [2], [2], [2]]
```

**Output:**

```id="u9n3dw"
[null, null, null, 1, -1, null, 1, null, -1]
```

---

## 💡 Description

We implement a HashMap using **separate chaining**:

* Use an array of buckets
* Each bucket stores a list of `(key, value)` pairs
* Use a hash function (`key % size`) to find the bucket index

If multiple keys map to the same index, they are stored in the same bucket (collision handling).

---

## 🧾 Solution (Python)

```python id="k7xv2r"
class MyHashMap:

    def __init__(self):
        self.size = 1000
        self.buckets = [[] for _ in range(self.size)]

    def hash(self, key):
        return key % self.size

    def put(self, key: int, value: int) -> None:
        index = self.hash(key)
        bucket = self.buckets[index]

        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket[i] = (key, value)
                return 
        bucket.append((key, value))

    def get(self, key: int) -> int:
        index = self.hash(key)
        bucket = self.buckets[index] 

        for k, v in bucket:
            if k == key:
                return v
        return -1

    def remove(self, key: int) -> None:
        index = self.hash(key)
        bucket = self.buckets[index]

        for i, (k, v) in enumerate(bucket):
            if k == key:
                bucket.pop(i)
                return
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:**

  * put → O(1) average, O(N) worst
  * get → O(1) average, O(N) worst
  * remove → O(1) average, O(N) worst

* **Space Complexity:** O(N)

---

## 🚀 Key Insight

Using **separate chaining**, we handle collisions by storing multiple elements in the same bucket instead of overwriting.

---

## ⚠️ Limitation

* Performance degrades if many collisions occur
* Choosing a good bucket size improves efficiency

---

## 🏷️ Tags

`Hashing` `Design` `Array`
