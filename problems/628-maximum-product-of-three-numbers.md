# 628. Maximum Product of Three Numbers

Given an integer array, find three numbers whose product is maximum and output the maximum product.

**Example 1:**

```
Input: [1,2,3]
Output: 6
```

**Example 2:**

```
Input: [1,2,3,4]
Output: 24
```

**Note:**

1. The length of the given array will be in range \[3,10^4\] and all elements are in the range \[-1000, 1000\].
2. Multiplication of any three numbers in the input won't exceed the range of 32-bit signed integer.

# Thoughts

We have to consider the negative numbers to get the max product. If the elements in nums are all positive, the rightmost three numbers is the answer. If the nums contains the negative numbers, the max product may be the leftmost two numbers and rightmose one number.

```
nums = [-1, -5, -100, 8, 2, 5, 9, 1, 7, 3, 4]

↓ (sort)

nums = [-100, -5, -1, 1, 2, 3, 4, 5, 7, 8, 9]
```

# Solution

```java
public class Solution {
    public int maximumProduct(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        return Math.max(
                nums[n - 1] * nums[n - 2] * nums[n - 3],
                nums[0] * nums[1] * nums[n - 1]    // consider the negative numbers
        );
    }
}
```



