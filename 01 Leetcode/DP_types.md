## Dynamic Programming Template Signatures and Examples

### 1. Subsequence DP (e.g., LIS, Word Break)
#### Signature: for i in range(1, n): for j in range(i):
```python
def subsequence_dp(nums):
    n = len(nums)
    dp = [1] * n
    for i in range(1, n):
        for j in range(i):
            if nums[j] < nums[i]:
                dp[i] = max(dp[i], dp[j] + 1)
    return max(dp)
```
### 2. Knapsack DP (0/1 or Unbounded)
#### Signature: for i in range(n): for w in range(W+1) or reversed(range(W+1))
```python
def knapsack_01(weights, values, capacity):
    n = len(weights)
    dp = [0] * (capacity + 1)
    for i in range(n):
        for w in range(capacity, weights[i] - 1, -1):
            dp[w] = max(dp[w], dp[w - weights[i]] + values[i])
    return dp[capacity]
```
### 3. Grid DP (e.g., Unique Paths, Minimum Path Sum)
#### Signature: for i in range(m): for j in range(n):
```python
def grid_dp(grid):
    m, n = len(grid), len(grid[0])
    dp = [[0]*n for _ in range(m)]
    dp[0][0] = grid[0][0]
    for i in range(m):
        for j in range(n):
            if i > 0: dp[i][j] = dp[i-1][j] + grid[i][j]
            if j > 0: dp[i][j] = min(dp[i][j], dp[i][j-1] + grid[i][j]) if dp[i][j] else dp[i][j-1] + grid[i][j]
    return dp[m-1][n-1]
```
### 4. Interval DP (e.g., Burst Balloons, Matrix Chain Multiplication)
#### Signature: for length in range(2, n+1): for left in range(...): for k in range(...):
```python
def interval_dp(nums):
    n = len(nums)
    nums = [1] + nums + [1]
    dp = [[0] * len(nums) for _ in range(len(nums))]
    for length in range(2, len(nums)):
        for left in range(0, len(nums) - length):
            right = left + length
            for k in range(left+1, right):
                dp[left][right] = max(dp[left][right], nums[left]*nums[k]*nums[right] + dp[left][k] + dp[k][right])
    return dp[0][len(nums)-1]
```
### 5. State Machine DP (e.g., Buy/Sell Stock with cooldown)
#### Signature: Custom states and transitions
```python
def stock_with_cooldown(prices):
    n = len(prices)
    if n <= 1: return 0
    hold, sold, rest = -prices[0], 0, 0
    for price in prices[1:]:
        prev_hold, prev_sold, prev_rest = hold, sold, rest
        hold = max(prev_hold, prev_rest - price)
        sold = prev_hold + price
        rest = max(prev_rest, prev_sold)
    return max(sold, rest)
```
### 6. Substring/Palindrome DP (e.g., Longest Palindromic Substring)
#### Signature: for length in range(2, n+1): for i in range(n-length+1):
```python
def palindrome_dp(s):
    n = len(s)
    dp = [[False]*n for _ in range(n)]
    start, max_len = 0, 1
    for i in range(n):
        dp[i][i] = True
    for length in range(2, n+1):
        for i in range(n - length + 1):
            j = i + length - 1
            if s[i] == s[j] and (length == 2 or dp[i+1][j-1]):
                dp[i][j] = True
                if length > max_len:
                    start, max_len = i, length
    return s[start:start+max_len]
```
