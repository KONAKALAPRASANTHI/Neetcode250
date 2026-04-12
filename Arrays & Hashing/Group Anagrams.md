# 🧩 Group Anagrams

## 📖 Problem Statement

Given an array of strings `strs`, group all anagrams together into sublists. You may return the output in any order.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

---

## 🔍 Example

**Input:**

```
["act","pots","tops","cat","stop","hat"]
```

**Output:**

```
[["hat"],["act","cat"],["stop","pots","tops"]]
```

---

## 💡 Description

The idea is to group words that have the same characters.
If we **sort each string**, all anagrams will produce the same sorted string.

Example:

* `"act"` → `"act"`
* `"cat"` → `"act"`

So, we use the **sorted string as a key** in a dictionary and group all matching words together.

---

## 🧾 Solution (Python)

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        hashmap = {}

        for string in strs:
            sorted_string = ''.join(sorted(string))

            if sorted_string in hashmap:
                hashmap[sorted_string].append(string)
            else:
                hashmap[sorted_string] = [string]
                
        return list(hashmap.values())
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N × K log K)

  * N = number of strings
  * K = maximum length of a string (sorting each string)

* **Space Complexity:** O(N × K)

---

## 🚀 Key Insight

Anagrams share the same **sorted representation**, which makes grouping efficient using a hashmap.

---

## 🏷️ Tags

`Array` `HashMap` `String`
