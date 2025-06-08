# LeetCode Array Problem Patterns (with Examples)

This is a comprehensive reference of array problem patterns on LeetCode, organized by technique with notes on how to identify them, when to apply, and classic examples.

---

## 1. Two Pointers

### When to Use
- Sorted arrays or strings
- Problems asking for pair/triplet/quads
- In-place operations (e.g., removing duplicates)

### Variants
- Opposite ends (e.g., left/right)
- Fast/slow pointers

### Examples
- [Two Sum II - Input Array Is Sorted (167)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
- [Remove Duplicates from Sorted Array (26)](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
- [Squares of a Sorted Array (977)](https://leetcode.com/problems/squares-of-a-sorted-array/)

---

## 2. Sliding Window

### When to Use
- Find the longest/shortest subarray or substring with certain properties
- Fixed-size window or dynamically shrinking/growing window

### Key Idea
- Move left/right pointers and maintain a window state (sum, count, set, map)

### Examples
- [Longest Substring Without Repeating Characters (3)](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [Maximum Average Subarray I (643)](https://leetcode.com/problems/maximum-average-subarray-i/)
- [Minimum Size Subarray Sum (209)](https://leetcode.com/problems/minimum-size-subarray-sum/)

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
- [Daily Temperatures (739)](https://leetcode.com/problems/daily-temperatures/)
- [Largest Rectangle in Histogram (84)](https://leetcode.com/problems/largest-rectangle-in-histogram/)
- [Trapping Rain Water (42)](https://leetcode.com/problems/trapping-rain-water/)

---

## 6. Cycle Detection (Floyd's Algorithm)

### When to Use
- Linked list or number sequence with repeated values
- Detecting loops or duplicates where values point to indices

### Examples
- [Linked List Cycle (141)](https://leetcode.com/problems/linked-list-cycle/)
- [Find the Duplicate Number (287)](https://leetcode.com/problems/find-the-duplicate-number/)
- [Happy Number (202)](https://leetcode.com/problems/happy-number/)

---

## 7. Binary Search on Answer

### When to Use
- Searching for a minimum/maximum possible value
- “Can you … in X time/space?” => Try X using binary search

### Examples
- [Koko Eating Bananas (875)](https://leetcode.com/problems/koko-eating-bananas/)
- [Capacity To Ship Packages Within D Days (1011)](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
- [Minimum Size Subarray Sum (209)](https://leetcode.com/problems/minimum-size-subarray-sum/) *(binary search + prefix sum)*

---

## 8. Hashing / Frequency Count

### When to Use
- Check for duplicates, counts, or frequency-based logic
- Often combined with sliding window

### Examples
- [Two Sum (1)](https://leetcode.com/problems/two-sum/)
- [Top K Frequent Elements (347)](https://leetcode.com/problems/top-k-frequent-elements/)
- [Longest Consecutive Sequence (128)](https://leetcode.com/problems/longest-consecutive-sequence/)

---

## 9. Greedy (Often with Sorting)

### When to Use
- Need optimal choice at every step
- Decisions depend only on current state

### Examples
- [Jump Game (55)](https://leetcode.com/problems/jump-game/)
- [Merge Intervals (56)](https://leetcode.com/problems/merge-intervals/)
- [Non-overlapping Intervals (435)](https://leetcode.com/problems/non-overlapping-intervals/)

---

## 10. In-Place Rearrangement

### When to Use
- Modify array without using extra space
- Problems involving rearranging numbers

### Examples
- [Move Zeroes (283)](https://leetcode.com/problems/move-zeroes/)
- [Sort Colors (75)](https://leetcode.com/problems/sort-colors/)
- [First Missing Positive (41)](https://leetcode.com/problems/first-missing-positive/)

---

## 11. Count + Math Patterns

### When to Use
- Count combinations, permutations, constraints-based counting
- Often mixed with prefix sums or hash maps

### Examples
- [Subarrays with K Different Integers (992)](https://leetcode.com/problems/subarrays-with-k-different-integers/)
- [Number of Subarrays With Bounded Maximum (795)](https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/)

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


