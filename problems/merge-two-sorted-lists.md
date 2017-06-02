# 21. Merge Two Sorted Lists

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

# Thought

```
e.g., given the two sorted lists => l1 = 1 -> 3 -> 5, l2 = 4 -> 5; 
      and the following numbers 4xx stands for object ids of nodes.

     434    438     439
l1 =  1  ->  3   ->  5  -> null

     435    437
l2 =  2  ->  4  -> null

                436 
head = current = 0  -> null


// after 1-iteration

      436    434    438    439            
head = 0  ->  1  ->  3  ->  5  -> null   (head.next = curr.next = l1)
             ^^^^^^^^^^^^^^^^^^^^^^^^^
      436    434    438    439
curr = 0  ->  1  ->  3  ->  5  -> null 

    438  439
l1 = 3 -> 5 -> null                      (l1 = l1.next)

      434   438   439
curr = 1 ->  3  -> 5  -> null            (curr = curr.next to keep the node value, i.e., 1)


// after 2-iteration

      436    434    435     437    
head = 0  ->  1  ->  2   ->  4  -> null  (curr.next = l2)
                    ^^^^^^^^^^^^^^^^^^^
      434    435    437
curr = 1  ->  2  ->  4

    437
l2 = 4 -> null                           (l2 = l2.next)

      435   437
curr = 2  -> 4  -> null


```

# Solution

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode head = new ListNode(0);
        ListNode curr = head;
        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                curr.next = l1;
                l1 = l1.next;
            } else {
                curr.next = l2;
                l2 = l2.next;
            }
            // moving forward to keep the val in this round
            curr = curr.next;
        }

        // handle the remainings
        if (l1 != null) curr.next = l1;
        if (l2 != null) curr.next = l2;

        // skip the head (dummy node)
        return head.next;
    }
}
```



