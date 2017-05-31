# 3. Longest Substring Without Repeating Characters

Given a string, find the length of the **longest substring **without repeating characters.

**Examples:**

Given `"abcabcbb"` , the answer is `"abc"`, which the length is 3.

Given `"bbbbb"`, the answer is `"b"`, with the length of 1.

Given `"pwwkew"`, the answer is `"wke"`, with the length of 3. Note that the answer must be a **substring**, `"pwke"` is a _subsequence_ and not a substring.

# Thinking

Two variables, `start` and `end`, representing respectively the start-index and end-index of the substring. Then increase the end value to collect the substring until repeating character occurs. Pay attention when moving the `start` pointer forward especially when `s[start] != s[end]`.

    if s[start] == s[end], just moving the start to start +1

      ↓ start = 0
    +-------------------------------+
    | a | b | c | a | b | c | b | b |
    +-------------------------------+
                  ↑ end = 3

    s[start] = s[end] = `a`, the following candidate of substring will be "bca"


    consider the following example, if s[start] != s[end], we need to skip the repeating chars, 

      ↓ start = 0
    +-------------------------------+
    | a | b | c | c | b | c | b | b |
    +-------------------------------+
                  ↑ end = 3 

    if we follow the above case to get next candidate, it will be "bcc". 
    this is wrong because it contains the repeating characters.
    we should keep moving until the two chars are the same, i.e., start = 2, end = 3.
    Since we always start += 1 before cut the substring, the substring will be substring(3:4), "c".  

# Solution

```java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int max = 0, start = 0;
        String substr = "";

        for (int end = 0; end < s.length(); end++) {
            if (substr.indexOf(s.charAt(end)) == -1) {
                // current char not found in substr, then append it to the substr
                substr += s.charAt(end);
            } else {
                // update the max length
                max = Math.max(max, substr.length());
                while (s.charAt(start) != s.charAt(end))
                    start += 1;
                start += 1;
                // slide the window of remainings
                substr = s.substring(start, end + 1);
            }
        }

        return Math.max(max, substr.length());
    }
}
```



