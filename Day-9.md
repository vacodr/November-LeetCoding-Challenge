# Maximum Difference Between Node and Ancestor
Given the root of a binary tree, find the maximum value V for which there exist different nodes A and B where V = |A.val - B.val| and A is an ancestor of B.

A node A is an ancestor of B if either: any child of A is equal to B, or any child of A is an ancestor of B.

link: https://leetcode.com/problems/maximum-difference-between-node-and-ancestor/

Problem type: Medium

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
    int maxDiff = 0;
    public int maxAncestorDiff(TreeNode root) {
        if (root == null) return 0;
        helper(root, root.val, root.val);
        return maxDiff;
    }
    public void helper(TreeNode root, int max, int min) {
        maxDiff = Math.max(maxDiff, Math.abs(max-root.val));
        maxDiff = Math.max(maxDiff, Math.abs(min-root.val));
        max = Math.max(max, root.val);
        min = Math.min(min, root.val);
        if (root.left != null) helper(root.left, max, min);
        if (root.right != null) helper(root.right, max, min);
    }
}
```
