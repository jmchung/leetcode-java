# 13. Roman to Integer

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

# Thought

The first thing we should know is the [roman numeral](https://en.wikipedia.org/wiki/Roman_numerals) \(I don't XD\), and convert the Character and corresponding Integer to a map. Normally, we can convert the roman numeral directly into integer, e.g., `X -> 10`, `V -> 5`.

But in some cases like `IX -> 10 - 1`, `IV -> 5 - 1` cannot sum up intuitively.

The idea is that we need to check the next character to determine the addition or subtraction of current character with sum.

# Solution

```
public class Solution {
    public int romanToInt(String s) {
        HashMap<Character, Integer> map = new HashMap<Character, Integer>() {{
            put('I', 1);
            put('V', 5);
            put('X', 10);
            put('L', 50);
            put('C', 100);
            put('D', 500);
            put('M', 1000);
        }};

        int res = 0;
        for (int i = 0; i < s.length(); i++) {
            // add guard condition to avoid the StringIndexOutOfBoundsException when grap the next character
            if (i < s.length() - 1 && map.get(s.charAt(i)) < map.get(s.charAt(i + 1)))
                res -= map.get(s.charAt(i));
            else res += map.get(s.charAt(i));
        }

        return res;
    }
}
```



