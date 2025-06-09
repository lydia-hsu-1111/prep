# First Missing Number Patterns & Templates

## 1. First Missing Positive (Leetcode 41)
### Pattern: Index as a Hash Key (In-place Bucket Sort)
```python
def firstMissingPositive(nums):
    n = len(nums)
    for i in range(n):
        while 1 <= nums[i] <= n and nums[nums[i]-1] != nums[i]:
            nums[nums[i]-1], nums[i] = nums[i], nums[nums[i]-1]
    for i in range(n):
        if nums[i] != i + 1:
            return i + 1
    return n + 1
```
- **Idea:** Place each number at its corresponding index `num - 1`.
- **Time:** O(n) | **Space:** O(1)

---

## 2. Missing Number (Leetcode 268)
### Pattern: Sum or XOR Trick
```python
def missingNumber(nums):
    n = len(nums)
    total = n * (n + 1) // 2
    return total - sum(nums)
```
**Or**
```python
def missingNumber(nums):
    xor = 0
    for i, num in enumerate(nums):
        xor ^= i ^ num
    return xor ^ len(nums)
```
- **Idea:** Use properties of arithmetic sum or XOR.
- **Time:** O(n) | **Space:** O(1)

---

## 3. Find All Numbers Disappeared in an Array (Leetcode 448)
### Pattern: Mark as Visited via Negation
```python
def findDisappearedNumbers(nums):
    for num in nums:
        index = abs(num) - 1
        nums[index] = -abs(nums[index])
    return [i + 1 for i, num in enumerate(nums) if num > 0]
```
- **Idea:** Use the sign of the elements to mark presence.
- **Time:** O(n) | **Space:** O(1) (excluding output)

---

## 4. Find Duplicate and Missing (Set Mismatch, Leetcode 645)
### Pattern: Frequency or Swap In-Place
```python
def findErrorNums(nums):
    for num in nums:
        i = abs(num) - 1
        nums[i] = -abs(nums[i])
    for i, num in enumerate(nums):
        if num > 0:
            return [abs(nums[i]), i + 1]
```
- **Idea:** First duplicate is where sign doesn't flip; missing is index of positive.
- **Time:** O(n) | **Space:** O(1)

---

## 5. Cyclic Sort Template (Generalized)
```python
def cyclic_sort(nums):
    i = 0
    while i < len(nums):
        correct = nums[i] - 1
        if 0 < nums[i] <= len(nums) and nums[i] != nums[correct]:
            nums[i], nums[correct] = nums[correct], nums[i]
        else:
            i += 1
    return nums
```
- **Idea:** Keep placing the numbers at their correct index until all are in place.

---

## Summary Table

| Problem | Method | Key Insight | Time | Space |
|--------|--------|-------------|------|-------|
| 41 | In-place Bucket | Swap to index `num-1` | O(n) | O(1) |
| 268 | Sum / XOR | Math trick | O(n) | O(1) |
| 448 | Negation | Use sign to mark visited | O(n) | O(1) |
| 645 | Negation | Similar to 448 | O(n) | O(1) |

