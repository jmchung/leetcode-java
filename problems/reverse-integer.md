# 7. Reverse Integer

Reverse digits of an integer.

**Example1: **x = 123, return 321  
**Example2: **x = -123, return -321

**Note:**

The input is assumed to be a 32-bit signed integer. Your function should **return 0 when the reversed integer overflows**.

# Thought

```
x will drop one digit (ones) in each iteration which divided by in 10
+-----------+
| 1 | 2 | 3 |  rev = 0 + 123 % 10 = 0 + 3 = 3, x = 123 / 10 = 12
+-----------+

          ↓ iterate
+-----------+
|   |   | 3 |
+-----------+
rev will increase one digit in each iteration which multiplied by 10, and keep the remainder

```

Getting the wrong answer for the first submission because I did not take the `overflow` into account. For example, given 1534236469 will raise the integer overflows, and we should return 0. Since I change the variable `rev` type from `int` to `long` to avoid reversed integer overflows. Lastly, check the valid range values of integer before return the reversed result.

# Solution

```java
public class Solution {
    public int reverse(int x) {
        long rev = 0;
        while (x != 0) {
            rev = rev * 10 + x % 10;
            x = x / 10;
        }

        if (rev < Integer.MIN_VALUE || rev > Integer.MAX_VALUE) return 0;
        return (int) rev;
    }
}
```



