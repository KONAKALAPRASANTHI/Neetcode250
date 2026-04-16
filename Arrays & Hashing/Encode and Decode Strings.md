# 🧩 Encode and Decode Strings

## 📖 Problem Statement

Design an algorithm to encode a list of strings into a single string and decode it back to the original list.

* `encode(strs)` → Encodes a list of strings into a single string
* `decode(s)` → Decodes the encoded string back to the original list

The decoded list must match the original input exactly.

---

## 🔍 Example

**Input:**

```id="q1m8zx"
["Hello","World"]
```

**Output:**

```id="n4v2kp"
["Hello","World"]
```

---

## 💡 Description

We use a **length-based encoding technique**:

* For each string, store its length followed by a delimiter (`#`) and the string itself
* Example: `"Hello"` → `"5#Hello"`
* Concatenate all encoded strings

While decoding:

* Read characters until `#` to get the length
* Extract the next `length` characters as the original string
* Repeat until the full string is processed

---

## 🧾 Solution (Python)

```python id="x7k2pd"
class Solution:

    def encode(self, strs: List[str]) -> str:
        encoded = ""
        for s in strs:
            encoded += str(len(s)) + "#" + s
        return encoded

    def decode(self, s: str) -> List[str]:
        res = []
        i = 0

        while i < len(s):
            j = i
            while s[j] != "#":
                j += 1

            length = int(s[i:j])
            word = s[j+1:j+1+length]

            res.append(word)
            i = j + 1 + length

        return res
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** O(N)
* **Space Complexity:** O(N)

---

## 🚀 Key Insight

By storing the **length of each string**, we avoid ambiguity even if the string contains special characters like `#`.

---

## ⚠️ Edge Cases

* Empty strings (`""`)
* Strings containing special characters (`#`, numbers, etc.)
* Large input size

---

## 🏷️ Tags

`String` `Design`
