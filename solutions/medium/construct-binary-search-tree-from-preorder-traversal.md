# Approach

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | Array, Stack, Tree, Binary Search Tree, Monotonic Stack, Binary Tree, Binary Search |
| LeetCode | [construct-binary-search-tree-from-preorder-traversal](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-07-08 |
| Next Review | 2026-07-09 |
| Interval | 1 day |
| Ease Factor | 2.5 |

## Solution

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
    public TreeNode bstFromPreorder(int[] preorder) {
        if (preorder == null || preorder.length == 0) {
            return null;
        }
        
        TreeNode root = new TreeNode(preorder[0]);
        Stack<TreeNode> st = new Stack();
        st.push(root);
        TreeNode prev = root;
        
        for (int i = 1; i < preorder.length; i++) {
            TreeNode temp = new TreeNode(preorder[i]);
            if (st.peek().val > preorder[i]) {
                st.peek().left = temp;
            } else {
                TreeNode parent = null;
                while (!st.isEmpty() && preorder[i] > st.peek().val) {
                    parent = st.pop();
                }
                
                parent.right = temp;
            }
            
            st.push(temp);
        }
        
        return root;
    }
}
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
