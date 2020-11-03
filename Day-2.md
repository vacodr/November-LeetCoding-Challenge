# 147. Insertion Sort List
Sort a linked list using insertion sort.

link: https://leetcode.com/problems/insertion-sort-list/

Problem type: Medium

## Code
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
    public ListNode insertionSortList(ListNode head) {
        ListNode h1 = new ListNode(-1), curr = head;
        
        while(curr != null) {
            ListNode temp = curr.next;
            ListNode prev = h1;
            ListNode nxt = h1.next;
            
            while(nxt != null) {
                if(nxt.val > curr.val)
                    break;
                prev = nxt;
                nxt = nxt.next;
            }
            
            curr.next = nxt;
            prev.next = curr;
            curr = temp;
        }
        
        return h1.next;
    }
}
'''
