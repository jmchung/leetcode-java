# 605. Can Place Flowers

Suppose you have a long flowerbed in which some of the plots are planted and some are not. However, flowers cannot be planted in adjacent plots - they would compete for water and both would die.

Given a flowerbed \(represented as an array containing 0 and 1, where 0 means empty and 1 means not empty\), and a number **n**, return if **n **new flowers can be planted in it without violating the no-adjacent-flowers rule.

**Example 1:**

```
Input: flowerbed = [1,0,0,0,1], n = 1
Output: True
```

**Example 2:**

```
Input: flowerbed = [1,0,0,0,1], n = 2
Output: False
```

**Note:**

1. The input array won't violate no-adjacent-flowers rule.
2. The input array size is in the range of \[1, 20000\].
3. **n **is a non-negative integer which won't exceed the input array size.

# Thoughts

```
Guard Conditions.

1. if the value of current item > 0 => pass
2. if i > 0, have to check the previous one's value
3. check the index boundary and check the value of last item
if passed above conditions, set the current item to 1 and increase the res.
```

# Solution

```java
public class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        int res = 0;
        for (int i = 0; i < flowerbed.length; i++) {
            if (flowerbed[i] > 0) continue;
            if (i > 0 && flowerbed[i - 1] > 0) continue;
            if (i < flowerbed.length - 1 && flowerbed[i + 1] > 0) continue;
            flowerbed[i] = 1;
            ++res;

            if (res >= n) return true;
        }

        return res >= n;
    }
}
```



