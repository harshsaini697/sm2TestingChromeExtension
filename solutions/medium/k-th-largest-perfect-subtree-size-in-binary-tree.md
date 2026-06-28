# K-th Largest Perfect Subtree Size in Binary Tree

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | Tree, Depth-First Search, Sorting, Binary Tree, Recursion |
| LeetCode | [k-th-largest-perfect-subtree-size-in-binary-tree](https://leetcode.com/problems/k-th-largest-perfect-subtree-size-in-binary-tree/) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-06-28 |
| Next Review | 2026-06-29 |
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
    private List<Integer> perfectSizes;
    public int kthLargestPerfectSubtree(TreeNode root, int k) {
        if (root == null) {
            return -1;
        }

        perfectSizes = new ArrayList();
        dfs(root);

        if (perfectSizes.size() < k) {
            return -1;
        }

        Collections.sort(perfectSizes, Collections.reverseOrder());

        return perfectSizes.get(k - 1);
    }

    private int dfs(TreeNode root) {
        if (root == null) {
            return 0;
        }

        int leftSize = dfs(root.left);
        int rightSize = dfs(root.right);

        if (leftSize == -1 || rightSize == -1 || leftSize != rightSize) {
            return -1;
        }

        int currentSize = 1 + leftSize + rightSize;
        perfectSizes.add(currentSize);
        return currentSize;
    }
}

// A perfect binary tree where root has both children and all leaves are same on the same level.
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
