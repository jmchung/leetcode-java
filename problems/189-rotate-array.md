# 189. Rotate Array

Rotate an array of _n_ elements to the right by _k_ steps.

For example, with _n_= 7 and _k_= 3, the array`[1,2,3,4,5,6,7]`is rotated to`[5,6,7,1,2,3,4]`.

# Thoughts

```
[1  2  3  4  5  6  7] (reverse all)


[7  6  5  4  3  2  1] (reverse 0 -> k-1)
 ^^^^^^^

[5  6  7  4  3  2  1] (reverse the remainings)
          ^^^^^^^^^^

[5  6  7  1  2  3  4]
```

# Solution

```java
public class Solution {
    public void rotate(int[] nums, int k) {
        k = k % nums.length;
        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, k-1);
        reverse(nums, k, nums.length-1);
    }

    private void reverse(int[] nums, int i, int j) {
        while (i < j) {
            swap(nums, i, j);
            i++;
            j--;
        }
    }

    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}
```



