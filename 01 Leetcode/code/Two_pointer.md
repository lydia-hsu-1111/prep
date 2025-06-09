## What Is It?

The **Two Pointers** technique uses two indices (pointers) to traverse a data structure — usually from opposite ends or with varying speed.

---

## When to Use

- Sorted arrays
- Comparing elements (e.g. palindrome check)
- Finding pairs (e.g. Two Sum)
- Merging two sorted lists
- Removing duplicates
- Partitioning problems

---

## Common Patterns

### 1. Opposite Ends (e.g. Two Sum II)
```python
left, right = 0, len(arr) - 1
while left < right:
    if arr[left] + arr[right] == target:
        return [left, right]
    elif arr[left] + arr[right] < target:
        left += 1
    else:
        right -= 1
```
### 2. Same Direction (e.g. Removing Duplicates)
```python
slow = 0
for fast in range(1, len(nums)):
    if nums[fast] != nums[slow]:
        slow += 1
        nums[slow] = nums[fast]
```
### 3. Fast & Slow Pointers (e.g. Linked List Cycle)
```python
slow = fast = head
while fast and fast.next:
    slow = slow.next
    fast = fast.next.next
    if slow == fast:
        return True
```
### 4. Two-Pointer where left starts after a search condition
```python
def two_pointer_template(nums):
    n = len(nums)
    left = 0
    right = 0

    # move right to the first valid start position
    while right < n and not is_valid_start(nums[right]):
        right += 1
    left = right  # start left from valid position

    result = 0

    while right < n:
        # expand right pointer while condition holds
        while right < n and is_valid_window(nums, left, right):
            # do your processing here
            result += process_window(nums, left, right)
            right += 1

        # shrink left to restore condition if needed
        while left < right and not is_valid_window(nums, left, right - 1):
            left += 1

        # or move both if you finished a segment
        if right < n and not is_valid_start(nums[right]):
            right += 1
            left = right

    return result
```
### 5. Sliding Window (e.g. Minimum Subarray Length)
```python
left = 0
for right in range(len(nums)):
    curr_sum += nums[right]
    while curr_sum >= target:
        min_len = min(min_len, right - left + 1)
        curr_sum -= nums[left]
        left += 1
```
