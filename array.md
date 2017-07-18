# 167. Two Sum II - Input array is sorted

Given an array of integers that is already _**sorted in ascending order**_, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers \(both index1 and index2\) are not zero-based.

You may assume that each input would have _exactly_ one solution and you may not use the same element twice.

**Input**: numbers={2, 7, 11, 15}, target=9

**Output**: index1=1, index2=2

# Thoughts

Similar to the [Two Sum](/problems/001-two-sum.md), we still can use the HashMap to store the visited numbers to find the specific target number. But if the given array has been sorted, we can simply employ two indicators to scan the array from both sides.

```
   i →
+-------------------------+
|  2  |  7  |  11  |  15  |
+-------------------------+
                     ← j
```

# Solution

```java
public class Solution {
    public int[] twoSum(int[] numbers, int target) {
        if (numbers == null || numbers.length == 0)
            return null;

        int i = 0;
        int j = numbers.length - 1;

        while (i < j) {
            int x = numbers[i] + numbers[j];
            if (x < target) {
                i++;
            } else if (x > target) {
                j--;
            } else {
                // x = target => index + 1
                return new int[]{i + 1, j + 1};
            }
        }

        return null;
    }
}
```



