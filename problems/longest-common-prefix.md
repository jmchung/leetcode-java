# 14. Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

# Thought

e.g., given an array of strings `["abcd", "abc", "abcdb"]` and the LCP is `"abc"`.

Pick the first element as base in outer loop, then iterate the remaining elements, and compare them with base in character.

Return the `strs[0]` to avoid getting wrong answer when given an array `["a"]`.

# Solution

```java
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";
        for (int i = 0; i < strs[0].length(); i++) {
            for (int j = 1; j < strs.length; j++) {
                // e.g., i >= strs[j].length() => [abcd, abc]
                if (i >= strs[j].length() || strs[0].charAt(i) != strs[j].charAt(i)) {
                    return strs[0].substring(0, i);
                }
            }
        }
        return strs[0]; // e.g., given the ["a"]
    }
}
```



