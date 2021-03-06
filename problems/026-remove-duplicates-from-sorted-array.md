# 26. Remove Duplicates from Sorted Array

Given a sorted array, remove the duplicates in place such that each element appear only _once_ and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

For example,  
Given input array _nums_=`[1,1,2]`,

Your function should return length =`2`, with the first two elements of _nums_ being`1`and`2`respectively. It doesn't matter what you leave beyond the new length.

# Thoughts

Skip to check the 1st element by `i == 0` and adding one to `idx`. Next compare current element with previous one in each iteration, `idx` incrementing by 1 and update the `nums[i]` with `nums[idx]` if two elements are different.

```
+-----------------+
|  1  |  1  |  2  |
+-----------------+
  i-1    i

skip to check
```

# Solution

```
public class Solution {
    public int removeDuplicates(int[] nums) {
        int idx = 0;
        for (int i = 0; i < nums.length; i++) 
            if (i == 0 || nums[i] != nums[i - 1])
                nums[idx++] = nums[i];

        return idx;
    }
}
```



