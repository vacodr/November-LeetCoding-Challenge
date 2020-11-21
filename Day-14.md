# 938. Range Sum of BST
Given the root node of a binary search tree, return the sum of values of all nodes with a value in the range [low, high].

Link: https://leetcode.com/problems/range-sum-of-bst/

Problem Type: Easy
## Code
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int rangeSumBST(TreeNode root, int low, int high) {
        if(root == null)
            return 0;
        int sum = root.val <= high && root.val >= low ? root.val : 0;
        int left = 0;
        int right = 0;
        if(root.left != null){
            left = rangeSumBST(root.left,low,high);
        } 
        if(root.right != null){
            right = rangeSumBST(root.right, low, high);
        }
        return sum + left + right;
    }
}
```
