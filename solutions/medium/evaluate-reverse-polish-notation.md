# Evaluate Reverse Polish Notation

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | Array, Math, Stack, String |
| LeetCode | [evaluate-reverse-polish-notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/?__cf_chl_f_tk=vnYxd1GRMRR1yNLlCGIHklk9fRv77COuF.sjhq4WD9I-1782938412-1.0.1.1-DYYgV7hWp3723gU3PPu.ZaugdhNyeZO9xXt9.x8RGbs) |

## Review

| Field | Value |
| --- | --- |
| Saved | 2026-07-01 |
| Next Review | 2026-07-02 |
| Interval | 1 day |
| Ease Factor | 2.5 |

## Solution

```java
class Solution {
    public int evalRPN(String[] tokens) {
        if(tokens == null || tokens.length == 0) return 0;
        
        Stack<Integer> st = new Stack<>();
        int x, y;
        for(int i = 0; i < tokens.length; i++) {
            String temp = tokens[i];
            if(temp.equals("+")) {
                st.add(st.pop() + st.pop());
            } else if(temp.equals("-")) {
                x = st.pop();
                y = st.pop();
                st.add(y - x);
            } else if(temp.equals("*")) {
                st.add(st.pop() * st.pop());
            } else if(temp.equals("/")) {
                x = st.pop();
                y = st.pop();
                st.add(y / x);
            } else {
                st.add(Integer.parseInt(temp));
            }
        }
        return st.pop();
    }
}
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
