# Count Number of Teams

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | Array, Dynamic Programming, Binary Indexed Tree, Segment Tree, Recursion |
| LeetCode | [count-number-of-teams](https://leetcode.com/problems/count-number-of-teams/description/) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-07-09 |
| Next Review | 2026-07-10 |
| Interval | 1 day |
| Ease Factor | 2.5 |

## Solution

```java
class Solution {
    public int numTeams(int[] rating) {

        int n = rating.length;
        int ans = 0;

        // Fixate one element and the find elements on left and right
        for (int j = 0; j < n; j++) {

            int leftSmaller = 0;
            int leftGreater = 0;

            int rightSmaller = 0;
            int rightGreater = 0;

            // explore left subsequence
            for (int i = 0; i < j; i++) {
                if (rating[i] < rating[j])
                    leftSmaller++;
                else
                    leftGreater++;
            }

            // explore right subsequenece
            for (int k = j + 1; k < n; k++) {
                if (rating[k] > rating[j])
                    rightGreater++;
                else
                    rightSmaller++;
            }

            ans += leftSmaller * rightGreater;
            ans += leftGreater * rightSmaller;
        }

        return ans;
    }
}
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
