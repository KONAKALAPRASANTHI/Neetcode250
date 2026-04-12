# 🧩 Longest Common Prefix

## 📖 Problem Statement
Given an array of strings `strs`, find the longest common prefix among them.  
If there is no common prefix, return an empty string `""`.

---

## 🔍 Example

**Input:**

["flower", "flow", "flight"]


**Output:**

"fl"


---

## 💡 Description
We take the first string as a reference prefix and compare it with the rest of the strings.  
If any string does not start with the current prefix, we reduce the prefix until it matches.  
This process continues until we find the common prefix or the prefix becomes empty.

---

## 🧾 Solution (Python)

```python
class Solution:
    def longestCommonPrefix(self, strs: List[str]) -> str:
        if not strs:
            return ""

        prefix = strs[0]

        for s in strs[1:]:
            while not s.startswith(prefix):
                prefix = prefix[:-1]
                if prefix == "":
                    return ""

        return prefix
```
⏱️ Complexity Analysis
Time Complexity: O(N × M)
Space Complexity: O(1)
