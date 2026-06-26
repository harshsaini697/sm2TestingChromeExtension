# Two Sum

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Easy |
| Language | Java |
| Tags | Array, Hash Table |
| LeetCode | [two-sum](https://leetcode.com/problems/two-sum/) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-06-26 |
| Next Review | 2026-06-27 |
| Interval | 1 day |
| Ease Factor | 2.5 |

## Solution

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap();
        for (int i = 0; i < nums.length; i++) {
            int comp = target - nums[i];
            if(map.containsKey(comp)) {
                return new int[] {i, map.get(comp)};
            }

            map.put(nums[i], i);
        }

        return new int[] {-1,-1};
    }
}
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
