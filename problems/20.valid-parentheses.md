# 20. Valid Parentheses

Given a string containing just the characters`'('`,`')'`,`'{'`,`'}'`,`'['`and`']'`, determine if the input string is valid.

The brackets must close in the correct order,`"()"`and`"()[]{}"`are all valid but`"(]"`and`"([)]"`are not.

# Thought

Leverage the LIFO \(last-in, first-out\) property of stack to keep the order of LEFT brackets, i.e., `'('`,`'{'` and `'['` , then pop the one element when meet the RIGHT ones. The question is how to know the popped item with current character are the valid parentheses?

One way is to create a hash map to store the corresponding bracket for each one such as `')' -> '('`. An alternative is to measure the difference of two chars in ascii value, e.g.,

```
Decimal     Glyph
-----------------
40          (
41          )
91          [
93          ]
123         {
125         }
```

# Solution

```java
public class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (ch == '(' || ch == '[' || ch == '{') {
                stack.push(ch);
            } else {
                if (stack.empty() || Math.abs(stack.pop() - ch) > 2) return false;
            }
        }

        return stack.empty();   // statck.empty represents brackets closed in the correct order
    }
}
```



