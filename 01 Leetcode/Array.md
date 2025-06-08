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
- [Subarray Sum Equals K (560)](https://leetcode.com/problems/subarray-sum-equals-k/)
- [Maximum Size Subarray Sum Equals k (325)](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)
- [Range Sum Query - Immutable (303)](https://leetcode.com/problems/range-sum-query-immutable/)

---

## 4. Monotonic Stack

### When to Use
- Next Greater/Smaller Element
- Histogram problems
- Trapping water

### Examples
- [Daily Temperatures (739)](https://leetcode.com/problems/daily-temperatures/)
- [Largest Rectangle in Histogram (84)](https://leetcode.com/problems/largest-rectangle-in-histogram/)
- [Trapping Rain Water (42)](https://leetcode.com/problems/trapping-rain-water/)

---

## 5. Binary Search on Answer

### When to Use
- Searching for a minimum/maximum possible value
- “Can you … in X time/space?” => Try X using binary search

### Examples
- [Koko Eating Bananas (875)](https://leetcode.com/problems/koko-eating-bananas/)
- [Capacity To Ship Packages Within D Days (1011)](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
- [Minimum Size Subarray Sum (209)](https://leetcode.com/problems/minimum-size-subarray-sum/) *(binary search + prefix sum)*

---

## 6. Hashing / Frequency Count

### When to Use
- Check for duplicates, counts, or frequency-based logic
- Often combined with sliding window

### Examples
- [Two Sum (1)](https://leetcode.com/problems/two-sum/)
- [Top K Frequent Elements (347)](https://leetcode.com/problems/top-k-frequent-elements/)
- [Longest Consecutive Sequence (128)](https://leetcode.com/problems/longest-consecutive-sequence/)

---

## 7. Greedy (Often with Sorting)

### When to Use
- Need optimal choice at every step
- Decisions depend only on current state

### Examples
- [Jump Game (55)](https://leetcode.com/problems/jump-game/)
- [Merge Intervals (56)](https://leetcode.com/problems/merge-intervals/)
- [Non-overlapping Intervals (435)](https://leetcode.com/problems/non-overlapping-intervals/)

---

## 8. In-Place Rearrangement

### When to Use
- Modify array without using extra space
- Problems involving rearranging numbers

### Examples
- [Move Zeroes (283)](https://leetcode.com/problems/move-zeroes/)
- [Sort Colors (75)](https://leetcode.com/problems/sort-colors/)
- [First Missing Positive (41)](https://leetcode.com/problems/first-missing-positive/)

---

## 9. Count + Math Patterns

### When to Use
- Count combinations, permutations, constraints-based counting
- Often mixed with prefix sums or hash maps

### Examples
- [Subarrays with K Different Integers (992)](https://leetcode.com/problems/subarrays-with-k-different-integers/)
- [Number of Subarrays With Bounded Maximum (795)](https://leetcode.com/problems/number-of-subarrays-with-bounded-maximum/)

---

## 📌 Decision Table

| Problem Type                         | Strategy                      |
|-------------------------------------|-------------------------------|
| Longest substring with condition    | Sliding Window                |
| Count subarrays with condition      | Prefix Sum + Hash Map         |
| Sorted + Pair logic                 | Two Pointers                  |
| Next Greater Element type           | Monotonic Stack               |
| Optimize Min/Max under constraint   | Binary Search on Answer       |
| Count or frequency logic            | Hash Map                      |
| Modify array in-place               | Two Pointers or Swapping      |
| Need to explore all combos          | Backtracking / DFS            |

---

## 🚀 Tips to Recognize Patterns

1. **Fixed-size window?** Likely sliding window.
2. **"Find k pairs" or similar?** Try heap or sorting + 2-pointers.
3. **Unsorted + need max/min efficiently?** Monotonic queue or deque.
4. **"Without extra space"?** Usually in-place with pointers.
5. **"What’s the smallest X that works?"** Binary Search on Answer.
6. **"Maximum length of subarray ..."?** Try prefix sum with hash map.

---

## ✅ Suggested Practice Order

| Pattern         | Easy Start | Challenge |
|----------------|------------|-----------|
| Two Pointers   | 26, 283    | 42, 76    |
| Sliding Window | 3, 209     | 76, 992   |
| Prefix Sum     | 303, 724   | 560, 1248 |
| Monotonic Stack| 496, 739   | 84, 42    |
| Binary Search  | 704, 278   | 875, 1011 |
| Hashing        | 1, 217     | 128, 974  |
| Greedy         | 455, 605   | 134, 406  |

