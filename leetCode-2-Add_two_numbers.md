# Add two numbers

 ```
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself

 

Example 1:

Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2:

Input: l1 = [0], l2 = [0]
Output: [0]

Example 3:

Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]

```

## java
> 時間複雜度O(n)，空間複雜度O(1)
   ```java
    class Solution {
        public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
            if (l1 == null && l2 == null) {
                return null;
            }
            if (l1 == null || l2 == null) {
                return l1 != null ? l1: l2;
            }
            ListNode l3;
            if (l1.val + l2.val < 10) {
                l3 = new ListNode(l1.val + l2.val);
                l3.next = addTwoNumbers(l1.next, l2.next);
            } else {
                l3 = new ListNode(l1.val + l2.val - 10);
                l3.next = addTwoNumbers(l1.next, addTwoNumbers(l2.next, new ListNode(1)));
            }
            return l3;
        }
    }
   ```
## php
   ```php
    class Solution {
        /**
         * @param ListNode $l1
         * @param ListNode $l2
         * @return ListNode
         */
        function addTwoNumbers($l1, $l2) {
            if (is_null($l1) && is_null($l2)) {
                return null;
            }
            if (is_null($l1) || is_null($l2)) {
                return is_null($l1) ? $l1 : $l2;
            }
            
            $l3 = null;
            if (($l1->val + $l2->val) < 10) {
                $l3 = new ListNode($l1->val + $l2->val);
                $l3->next = $this->addTwoNumbers($l1->next, $l2->next);
            } else {
                $l3 = new ListNode(($l1->val + $l2->val) - 10);
                $l3->next = $this->addTwoNumbers($l1->next, $this->addTwoNumbers($l2->next, new ListNode(1)));
            }
            return $l3;
        }
    }
   ```
