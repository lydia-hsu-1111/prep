# LeetCode Array Problem Patterns (with Examples)

This is a comprehensive reference of array problem patterns on LeetCode, organized by technique with notes on how to identify them, when to apply, and classic examples.

---

## 1. [Two Pointers](./code/Two_pointer.md)

### When to Use
- Sorted arrays or strings
- Problems asking for pair/triplet/quads
- In-place operations (e.g., removing duplicates)

### Variants
- Opposite ends (e.g., left/right)
- Fast/slow pointers

### Examples
- Two Sum II - Input Array Is Sorted (LC167)
- Remove Duplicates from Sorted Array (LC26)
- Squares of a Sorted Array (LC977)
---

## 2. Sliding Window

### When to Use
- Find the longest/shortest subarray or substring with certain properties
- Fixed-size window or dynamically shrinking/growing window

### Key Idea
- Move left/right pointers and maintain a window state (sum, count, set, map)

### Examples
- Longest Substring Without Repeating Characters (LC3)
- Maximum Average Subarray I (LC643)
- Minimum Size Subarray Sum (LC209)
---

## 3. Prefix Sum

### When to Use
- Subarray sum problems
- Need to quickly get the sum of a subarray
- Also supports 2D variants (matrix region sum)

### Examples
- Subarray Sum Equals K (LC560)

---

## 4. Three Pointers

### When to Use
- Problems involving **triplets** or sorted arrays (3Sum, sort colors)
- Tracking **low**, **mid**, and **high** indices simultaneously

### Examples
- 3Sum (LC15)
- 3Sum Closest (LC16)
- Sort Colors (LC75) — [Dutch National Flag](./code/Three_pointer_sorting.md)

---

## 5. Monotonic Stack

### When to Use
- Next Greater/Smaller Element
- Histogram problems
- Trapping water

### Examples
- Daily Temperatures (LC739)
- Largest Rectangle in Histogram (LC84)
- Trapping Rain Water (LC42)

---

## 6. Cycle Detection (Floyd's Algorithm)

### When to Use
- Linked list or number sequence with repeated values
- Detecting loops or duplicates where values point to indices

### Examples
- [Linked List Cycle (LC141)
- Find the Duplicate Number (LC287)
-- SOLUTION I: [Floyd_Tortoise_and_Hare](./code/Floyd_Tortoise_and_Hare.md); SOLUTION II: [Binary Search](./code/BS_cycle.md)
- Happy Number (LC202)

---

## 7. Binary Search on Answer

### When to Use
- Searching for a minimum/maximum possible value
- “Can you … in X time/space?” => Try X using binary search

### Examples
- Koko Eating Bananas (LC875)
- Capacity To Ship Packages Within D Days (LC1011)
---

## 8. Hashing / Frequency Count

### When to Use
- Check for duplicates, counts, or frequency-based logic
- Often combined with sliding window

### Examples
- Two Sum (LC1)
- Top K Frequent Elements (LC347)
- Longest Consecutive Sequence (LC128)
---

## 9. Greedy (Often with Sorting)

### When to Use
- Need optimal choice at every step
- Decisions depend only on current state

### Examples
- [Jump Game (LC55)](./code/Jump_game.md)
- Merge Intervals (56)
- Non-overlapping Intervals (435)

---

## 10. In-Place Rearrangement

### When to Use
- Modify array without using extra space
- Problems involving rearranging numbers

### Examples
- Move Zeroes (LC283)
- [First Missing Positive (LC41)](./code/First_missing_positive)

---

## 11. [Count + Math Patterns](./code/Count_math_pattern.md)

### When to Use
- Count combinations, permutations, constraints-based counting
- Often mixed with prefix sums or hash maps

### Examples
- Subarrays with K Different Integers (LC992)
- Number of Subarrays With Bounded Maximum (LC795)

---

## Decision Table

| Problem Type                         | Strategy                      |
|-------------------------------------|-------------------------------|
| Longest substring with condition    | Sliding Window                |
| Count subarrays with condition      | Prefix Sum + Hash Map         |
| Sorted + Pair logic                 | Two Pointers / Three Pointers |
| Next Greater Element type           | Monotonic Stack               |
| Optimize Min/Max under constraint   | Binary Search on Answer       |
| Detect loops or repeats             | Cycle Detection (Floyd's)     |
| Count or frequency logic            | Hash Map                      |
| Modify array in-place               | Two/Three Pointers or Swap    |
| Need to explore all combos          | Backtracking / DFS            |

---

## Tips to Recognize Patterns

1. **Fixed-size window?** Likely sliding window.
2. **"Find k pairs" or similar?** Try heap or sorting + 2-pointers.
3. **Unsorted + need max/min efficiently?** Monotonic queue or deque.
4. **"Without extra space"?** Usually in-place with pointers.
5. **"What’s the smallest X that works?"** Binary Search on Answer.
6. **"Maximum length of subarray ..."?** Try prefix sum with hash map.
7. **Repeated steps from element to index (nums[nums[i]])?** Likely cycle detection.


