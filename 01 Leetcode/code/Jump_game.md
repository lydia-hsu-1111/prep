Track the farthest index you can reach so far. If at any index, the farthest you can reach is less than the current index, you can’t proceed.
```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        farthest = 0
        for i in range(len(nums)):
            if i > farthest:
                return False
            farthest = max(farthest, i + nums[i])
        return True
```
