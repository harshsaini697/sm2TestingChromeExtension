# Valid Parenthesis String

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | String, Dynamic Programming, Stack, Greedy |
| LeetCode | [valid-parenthesis-string](https://leetcode.com/problems/valid-parenthesis-string/submissions/2053910973/) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-07-02 |
| Next Review | 2026-07-03 |
| Interval | 1 day |
| Ease Factor | 2.5 |

## Solution

```java
class Solution {
    public boolean checkValidString(String s) {
        Stack<Integer> leftStack = new Stack<>();
        Stack<Integer> starStack = new Stack<>();

        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            if (c == '(') {
                leftStack.push(i);
            } else if (c == '*') {
                starStack.push(i);
            } else if (c == ')') {
                if (!leftStack.isEmpty()) {
                    leftStack.pop();
                } else if (!starStack.isEmpty()) {
                    starStack.pop();
                } else {
                    return false;
                }
            }
        }

        while (!leftStack.isEmpty() && !starStack.isEmpty()) {
            if (leftStack.peek() > starStack.peek()) {
                return false;
            }
            
            leftStack.pop();
            starStack.pop();
        }

        return leftStack.isEmpty();
    }
}
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
