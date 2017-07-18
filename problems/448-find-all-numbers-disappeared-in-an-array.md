# 448. Find All Numbers Disappeared in an Array

Given an array of integers where 1 ≦ a\[i\] ≦_n_\(_n_= size of array\), some elements appear twice and others appear once.

Find all the elements of \[1,n\] inclusive that do not appear in this array.

Could you do it without extra space and in O\(_n_\) runtime? You may assume the returned list does not count as extra space.

**Example:**

```
Input:
[4,3,2,7,8,2,3,1]

Output:
[5,6]
```

# Thoughts

Because 1 ≦ a\[i\] ≦_n_\(_n_= size of array\), we can map the number to corresponding location in array and mark it with negative. Then scan the array again and add the index of number which is positive.

    idx       0    1    2    3    4    5    6    7
    arr   [   4,   3,   2,   7,   8,   2,   3,   1  ]

    ↓ e.g., 1st element `4`

    idx       0    1    2    3    4    5    6    7
    arr   [    ,    ,    ,  -4,    ,    ,    ,      ]


# Solution

```java
public class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> numbers = new ArrayList<>();

        for (int num : nums)
            nums[Math.abs(num) - 1] = -Math.abs(nums[Math.abs(num) - 1]);

        for (int i = 0; i < nums.length; i++)
            if (nums[i] > 0) numbers.add(i + 1);
        
        return numbers;
    }
}
```



