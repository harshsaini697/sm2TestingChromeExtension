# 3Sum

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | Array, Two Pointers, Sorting |
| LeetCode | [3sum](https://leetcode.com/problems/3sum/) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-06-22 |
| Next Review | 2026-06-23 |
| Interval | 1 day |
| Ease Factor | 2.5 |

## Solution

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        if (nums == null || nums.length == 0){
            return new ArrayList<List<Integer>>();
        }

        List<List<Integer>> res = new ArrayList<>();
        // two pointer with sorting
        Arrays.sort(nums);
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > 0) break;
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            int j = i + 1;
            int k = nums.length - 1;

            while(j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                if (sum == 0) {
                    res.add(Arrays.asList(nums[i], nums[j], nums[k]));
                    j++;
                    k--;
                    while(j < k && nums[j] == nums[j - 1]) j++;
                    while(j < k && nums[k] == nums[k + 1]) k--;
                } else if (sum < 0) {
                    j++;
                } else {
                    k--;
                }
            }
        }
        
        return res;
    }
}

//something else
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
