# 27. Remove Element

Given an array and a value, remove all instances of that value in place and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example:**  
Given input array _nums_=`[3,2,2,3]`,_val_=`3`

Your function should return length = 2, with the first two elements of _nums_ being 2.

# Thoughts

Two pointers.

# Solution

```java
public class Solution {
    public int removeElement(int[] nums, int val) {
        int idx = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[idx++] = nums[i];
            }
        }

        return idx;
    }
}
```



