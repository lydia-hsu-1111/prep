# How to Think About Tricky Sliding Window Problems (LeetCode 795, 992, etc.)

Mastering problems like LeetCode 795, 992, and 41 requires spotting patterns and rephrasing problems. Here’s a guide to develop that intuition.

---

## 1. Clarify the Problem Goal

- Are you **counting** subarrays?
- Are you **finding** max/min length?
- Is the problem about **distinct elements**, **value ranges**, or **frequency**?

🟢 Example:  
**Leetcode 795** → Count subarrays where max ∈ `[left, right]`.

---

## 2. Use “At Most K” Trick

> 💡 Powerful trick:  
> `count(exactly_k) = count(at_most_k) - count(at_most_k - 1)`

### Use when:
- Problem says **"exactly K"** distinct or odd or sum, etc.
  
### 🔁 Common Problems:
- Leetcode 992: Subarrays with Exactly K Distinct
- Leetcode 1248: Count of Subarrays with Odd Numbers
- Leetcode 930: Binary Subarrays with Sum
- Leetcode 904: Fruit Into Baskets

---

## 3. Bounded Value Range Strategy

Use this when the subarray must follow a **value constraint** (like max ∈ `[left, right]`).

### Strategy:
- Keep track of the **last index where constraint broke**
- Use a **sliding window** from last invalid point
- Count all subarrays ending at current index

### 🧪 Example: Leetcode 795
```python
def count(bound):
    res = 0
    curr = 0
    for num in nums:
        if num <= bound:
            curr += 1
        else:
            curr = 0
        res += curr
    return res

result = count(right) - count(left - 1)
