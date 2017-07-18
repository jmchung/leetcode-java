# 219. Contains Duplicate II

Given an array of integers and an integer _k_, find out whether there are two distinct indices _i_ and _j_ in the array such that **nums\[i\] = nums\[j\] **and the **absolute **difference between _i_ and _j_ is at most _k_.

**Example:**

```
nums = [1, 2, 3, 4, 1], k = 3; 
nums[0] = nums[4] = 1, j = 4, i = 0 => dist(i,j) > k => false

nums = [1, 2, 3, 4, 1], k = 4; 
nums[0] = nums[4] = 1 , j = 4, i = 0 => true
```

# Thoughts

Use HashMap to keep the value and index of visited item .

# Solution

```java
public class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(nums[i]) && (i - map.get(nums[i])) <= k) {
                return true;
            } else {
                map.put(nums[i], i);
            }

        }

        return false;
    }
}
```



