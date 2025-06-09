```python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        n = len(nums)

        # Step 1: Place each number in its correct index if possible
        for i in range(n):
            while 1 <= nums[i] <= n and nums[nums[i] - 1] != nums[i]:
                correct_idx = nums[i] - 1
                nums[i], nums[correct_idx] = nums[correct_idx], nums[i]

        # Step 2: Find the first place where index + 1 != value
        for i in range(n):
            if nums[i] != i + 1:
                return i + 1

        return n + 1
```
