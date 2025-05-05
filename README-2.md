# LeetCode Problem 2: Add Two Numbers

## Problem Description
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each node contains a single digit. Add the two numbers and return the sum as a linked list.

### Example
**Input:**  
`l1 = [2,4,3]` (represents 342)  
`l2 = [5,6,4]` (represents 465)  

**Output:**  
`[7,0,8]` (represents 807)  

**Explanation:**  
342 + 465 = 807

## Solution Approach
### Algorithm
1. Initialize a dummy head node and current pointer
2. Initialize carry to 0
3. Loop through both lists until all nodes and carry are processed:
   - Sum the current digits from both lists plus carry
   - Calculate new digit (sum % 10) and new carry (sum / 10)
   - Create new node with the digit value
   - Advance all pointers
4. Return the list after dummy head

### Complexity Analysis
- **Time Complexity:** O(max(m,n))  
  (Where m and n are lengths of the two lists)
- **Space Complexity:** O(max(m,n))  
  (For the resulting linked list)

## Solution Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode current = dummyHead;
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
            
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
        }
        
        return dummyHead.next;
    }
}
