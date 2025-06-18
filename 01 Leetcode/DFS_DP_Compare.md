## LeetCode 516 (Longest Palindromic Subsequence) solved two ways:

### Top-down DFS + Memoization

Idea:
- Use two pointers, left and right.
- If s[left] == s[right], then the answer includes these two chars + answer for substring inside (left+1, right-1).
- Else, skip either left or right char and take max.
```python
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        from functools import lru_cache
        
        n = len(s)

        @lru_cache(None)
        def dfs(left, right):
            if left > right:
                return 0
            if left == right:
                return 1
            if s[left] == s[right]:
                return 2 + dfs(left+1, right-1)
            else:
                return max(dfs(left+1, right), dfs(left, right-1))
        
        return dfs(0, n-1)
```

### Bottom-up DP (Tabulation)

- We build a 2D table dp where dp[i][j] represents the length of the longest palindromic subsequence in substring s[i:j+1].
- Base case: single chars are palindrome of length 1: dp[i][i] = 1.
- Fill the table from smaller substrings to larger substrings.
```python
class Solution:
    def longestPalindromeSubseq(self, s: str) -> int:
        n = len(s)
        dp = [[0]*n for _ in range(n)]
        
        # Single chars are palindrome of length 1
        for i in range(n):
            dp[i][i] = 1
        
        # Fill dp for substrings of length 2 to n
        for length in range(2, n+1):
            for i in range(n-length+1):
                j = i + length - 1
                if s[i] == s[j]:
                    if length == 2:
                        dp[i][j] = 2
                    else:
                        dp[i][j] = 2 + dp[i+1][j-1]
                else:
                    dp[i][j] = max(dp[i+1][j], dp[i][j-1])
        
        return dp[0][n-1]
```
