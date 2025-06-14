1. Number of Islands
```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        count = 0
        m = len(grid)
        n = len(grid[0])
        
        def dfs(x,y):
            directions = [(1,0),(-1,0),(0,1),(0,-1)]
            for dx, dy in directions:
                if (0<=x+dx<m) and (0<=y+dy<n) and (grid[x+dx][y+dy] == '1'):
                    grid[x+dx][y+dy] = '*'
                    dfs(x+dx,y+dy)

        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    count += 1
                    grid[i][j] = '*'
                    dfs(i,j)
        return count
```
2. Word Search
```python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        m = len(board)
        n = len(board[0])

        def dfs(x,y,ind):
            if ind == len(word): 
                return True           
            if x < 0 or x >= m or y < 0 or y >= n or board[x][y] != word[ind]:
                return False
            
            ind +=1
            temp = board[x][y]
            board[x][y] = '*'
            found = dfs(x+1, y, ind) or dfs(x-1, y, ind) or dfs(x, y+1, ind) or dfs(x, y-1, ind) 
            board[x][y] = temp

            return found
        
        for i in range(m):
            for j in range(n):
                if board[i][j] == word[0]and dfs(i,j,0):
                    return True

        return False
```
3. Coin Change
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        coins.sort()
        
        from functools import lru_cache
        @lru_cache(None)

        def dfs(amount):
            if amount == 0:
                return 0
            if amount < 0:
                return float("inf")
            if amount in coins:
                return 1
            return min([dfs(amount-c) for c in coins]) + 1

        res = dfs(amount)
        return res if res != float('inf') else -1
```
4. Loud and Rich
```python
from collections import defaultdict

class Solution:
    def loudAndRich(self, richer: List[List[int]], quiet: List[int]) -> List[int]:
        n = len(quiet)
        graph = defaultdict(list)

        # Build graph: edge a -> b if a is richer than b
        for a, b in richer:
            graph[b].append(a)

        answer = [-1] * n

        def dfs(i):
            if answer[i] != -1:
                return answer[i]
            
            min_quiet = quiet[i]
            min_person = i

            for nei in graph[i]:
                cand = dfs(nei)
                if quiet[cand] < min_quiet:
                    min_quiet = quiet[cand]
                    min_person = cand

            answer[i] = min_person
            return min_person

        for i in range(n):
            dfs(i)

        return answer
```
Key steps:

- Post-order DFS: first go deep, then make decisions on the way up.

- Memoize the result per node so you don’t recompute.

- Naturally handle multiple paths and cycles (if they existed, but they don't here).
  
- Note: Don’t mix nonlocal mutable state and @lru_cache.
  
