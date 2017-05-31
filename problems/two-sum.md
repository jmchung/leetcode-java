# 1. Two Sum

Given an array of integers, return **indices **of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly **one solution, and you may not use thesameelement twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

# 解題

```java
public class Solution {
    // the naive way to get the combination of target can use loop-in-loop, if nums[i] + nums[j] = target the return.
    // however, the complexity of above approach is O(n^2).
    // here we can leverage a hashmap to record the visited number and find out the target in one loop of nums.
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();    // <value, visited-index>
        int[] result = new int[2];

        for (int i = 0; i < nums.length; i++) {
            if (map.containsKey(nums[i])) {
                // let v = nums[i] and x = target - v,
                // if map contains x, then x must be visited before, target = index(x) + index(v)
                int index = map.get(nums[i]);
                result[0] = index ;
                result[1] = i;
                break;
            } else {
                map.put(target - nums[i], i);
            }
        }

        return result;
    }
}
```



