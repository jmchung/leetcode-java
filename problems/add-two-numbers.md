# 2. Add Two Numbers

# 題目

You are given two **non-empty **linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Input:  **\(2 -&gt; 4 -&gt; 3\) + \(5 -&gt; 6 -&gt; 4\)  
**Output: **7 -&gt; 0 -&gt; 8

# 解題

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        // use a dummy node that points to the head/tail can help reduce many of the checks,
        // and current acting as a cursor to the returned singly-linked list.
        // +------------+      +-----------+
        // | dummy node | ---> | sum % 10  | ---> ...
        // +------------+      +-----------+
        //              ^ the real result list is in dummy.next.
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        int carry = 0;
        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            // carry digit != 0 if sum > 9, will be added in next round with val of l1 and l2
            carry = sum / 10;
            sum = sum % 10;
            current.next = new ListNode(sum);
            current = current.next;
        }
        return dummy.next;
    }
}
```

# 數字相加解法

An alternative is that we can  balala

```java
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        int carry = 0;
        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            // carry digit != 0 if sum > 9, will be added in next round with val of l1 and l2
            carry = sum / 10;
            sum = sum % 10;
            current.next = new ListNode(sum);
            current = current.next;
        }
        return dummy.next;
    }
}
```



