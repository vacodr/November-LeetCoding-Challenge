## 445. Add Two Numbers II
You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Follow up:
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

link: https://leetcode.com/problems/add-two-numbers-ii/

Problem type: Medium
# Code
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
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        Stack<Integer> s1 = listToStack(l1);
        Stack<Integer> s2 = listToStack(l2);
        
        ListNode head = null;
        int carry = 0;
        while(s1.size() > 0 || s2.size() > 0 || carry != 0) {
            int sum = carry;
            if(s1.size() > 0) sum += s1.pop();
            if(s2.size() > 0) sum += s2.pop();
            ListNode newNode = new ListNode(sum % 10);
            newNode.next = head;
            head = newNode;
            carry = sum / 10;
        }
        
        return head;
    }
    
    private Stack<Integer> listToStack(ListNode l) {
        Stack<Integer> stack = new Stack();
        while(l != null) {
            stack.add(l.val);
            l = l.next;
        }
        return stack;
    }
}
```
