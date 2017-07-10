# 283. Move Zeroes

Given an array`nums`, write a function to move all`0`'s to the end of it while maintaining the relative order of the non-zero elements.

For example, given`nums = [0, 1, 0, 3, 12]`, after calling your function,`nums`should be`[1, 3, 12, 0, 0]`.

**Note**:

1. You must do this **in-place **without making a copy of the array.
2. Minimize the total number of operations.

# Thoughts

Again, use two indicators, one is the index in loop, the other represents zero number. Then swap the values when meet the non-zero number \(because we want to move all 0's to the end\), and update the zero-idx.

```asciidoc
  ↓ for-loop-idx
+--------------------+
| 0 | 1 | 0 | 3 | 12 |
+--------------------+
  ^ z-idx
```

# Solution

```java
public class Solution {
    public void moveZeroes(int[] nums) {
        // j: zero-index
        for (int i = 0, j = 0; i < nums.length && j < nums.length; i++) {
            if (nums[i] != 0) {    // swap
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
                j++;    // update the zero-idx
            }
        }
    }
}
```



