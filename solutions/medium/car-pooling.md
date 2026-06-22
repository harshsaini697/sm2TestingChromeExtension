# Intuition

## Problem

| Field | Value |
| --- | --- |
| Difficulty | Medium |
| Language | Java |
| Tags | Array, Sorting, Heap (Priority Queue), Simulation, Prefix Sum, Greedy, Hash Table, Tree, Dynamic Programming, Iterator, Bucket Sort, Hash Function, Suffix Array, Queue, Math, Two Pointers, Counting Sort, Ordered Set, Sliding Window, Counting, Matrix, Memoization, Recursion, Brainteaser, Binary Tree, Stack, Depth-First Search, Binary Search, Priority Queue |
| LeetCode | [car-pooling](https://leetcode.com/problems/car-pooling/description/) |

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
    public boolean carPooling(int[][] trips, int capacity) {
        if (capacity == 0) {
            return true;
        } 
        
        if (trips.length == 0 || trips[0].length == 0) {
            return true;
        }

        Arrays.sort(trips, (a, b) -> Integer.compare(a[1], b[1]));

        PriorityQueue<Pair<Integer,Integer>> pq =
            new PriorityQueue<>(
                (p1, p2) ->
                    Integer.compare(
                        p1.getValue(),
                        p2.getValue()
                    )
            );

        int occupied = 0;

        for (int[] trip : trips) {

            int passengers = trip[0];
            int start = trip[1];
            int end = trip[2];

            while (!pq.isEmpty() &&
                pq.peek().getValue() <= start) {

                Pair<Integer,Integer> completed = pq.poll();

                occupied -= completed.getKey();
            }

            occupied += passengers;

            if (occupied > capacity) {
                return false;
            }

            pq.offer(new Pair<>(passengers, end));
        }

        return true;
    }
}

// [Pair<Psngers, DropOffLocation>] -> 
// [<2,3> , <3, 7>]
// []
```

## Notes

- Approach:
- Time Complexity:
- Space Complexity:
