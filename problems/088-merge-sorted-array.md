# 88. Merge Sorted Array

Given two sorted integer arrays _nums1_ and _nums2_, merge _nums2_ into _nums1_ as one sorted array.

**Note**:

You may assume that _nums1_ has enough space \(size that is greater or equal to _m_ + _n_\) to hold additional elements from _nums2_. The number of elements initialized in _nums1_ and _nums2_ are _m_ and _n_ respectively.

# Thoughts

The following example illustrates the solution proposed by [Andy](https://github.com/leetcoders/LeetCode-Java/blob/master/MergeSortedArray.java).

\(1\) identify the index of last element in arrays, `i = m - 1 = 2`, and `j = n - 1 = 1`.

\(2\) identify the last position of space, `x = m + n - 1 = 4`.

\(3\) compare `nums1[i]` with `nums2[j]` to determine the proper location in `nums1`. \(copy the value\)

the main idea like he said, **from back to forth**.

```java
int[] nums1 = {1, 2, 6, 0, 0}, m=3

             ← i
+-----------------------------+
|  1  |  2  |  6  |  -  |  -  |
+------------------------------


int[] nums2 = {4, 5}, n=2

       ← j
+-----------+
|  4  |  5  |
+-----------+
```

My original plan was to simply merge two arrays then perform the quick-sort on nums1. But I think his approach is more elegant and succinct.

# Solution

```java
public class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int x = m + n - 1;
        while (i >= 0 && j >= 0)
            if (nums1[i] >= nums2[j]) nums1[x--] = nums1[i--];
            else nums1[x--] = nums2[j--];
        while (j >= 0) nums1[x--] = nums2[j--];
    }
}
```



