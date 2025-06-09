```python
def findDuplicate(nums):
    # Step 1: Detect cycle using Floyd's algorithm
    slow = nums[0]
    fast = nums[0]
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break

    # Step 2: Find the entrance to the cycle
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]

    return slow
```
