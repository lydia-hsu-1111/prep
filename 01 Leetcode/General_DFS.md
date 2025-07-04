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
3. Loud and Rich (no memoization)
```python
from collections import defaultdict
class Solution:
    def loudAndRich(self, richer: List[List[int]], quiet: List[int]) -> List[int]:
        n = len(quiet)
        graph = defaultdict(list)
        output = [0]*n
        
        for a, b in richer:
            graph[b].append(a)

        def dfs(i):
            nonlocal quietest
            nonlocal person
            quietest = min(quietest, quiet[i])
            if quietest == quiet[i]:
                person = i
            for neighbor in graph[i]:
                dfs(neighbor)
                
        for i in range(n):
            quietest = quiet[i]
            person = i
            dfs(i)
            output[i] = person
        return output
```
3. Loud and Rich (memoization)
```python
from collections import defaultdict

class Solution:
    def loudAndRich(self, richer: List[List[int]], quiet: List[int]) -> List[int]:
        n = len(quiet)
        graph = defaultdict(list)
        output = [0] * n
        
        for a, b in richer:
            graph[b].append(a)
        
        memo = {}  # memo[i] = person with min quietness for person i

        def dfs(i):
            if i in memo:
                return memo[i]

            quietest = quiet[i]
            person = i

            for neighbor in graph[i]:
                cand = dfs(neighbor)
                if quiet[cand] < quietest:
                    quietest = quiet[cand]
                    person = cand

            memo[i] = person
            return person

        for i in range(n):
            output[i] = dfs(i)

        return output
```
Key notes:

- Don’t mix nonlocal mutable state and @lru_cache.
- Even though the logic is correct in a clean tree without memoization, the graph is a DAG (Directed Acyclic Graph) — which means:

    - Some nodes are visited multiple times from different people.

    - Without memoization, the same subgraphs are re-traversed repeatedly.

    - That can cause:

        - Redundant work (inefficient).

        - Incorrect results if a better (quieter) candidate exists in a previously traversed path.
- Global or nonlocal variables for values are not needed when each recursive call returns its own values.
     
### Knapsack type of questions - crossing the bridge between DFS and DP
#### Knapsack prototype
```python
# 0/1 Knapsack (Recursive with Memo)
def knapsack_01(i, w):
    if i == len(weights) or w == 0:
        return 0
    if (i, w) in memo:
        return memo[(i, w)]

    # Skip item
    res = knapsack_01(i + 1, w)

    # Take item if it fits
    if weights[i] <= w:
        res = max(res, values[i] + knapsack_01(i + 1, w - weights[i]))

    memo[(i, w)] = res
    return res
```
Note: You could write a backtracking function like this, but this explores all subsets explicitly, which is much slower.
```python
def dfs(i, w, path):
    if w > capacity:
        return
    if i == len(weights):
        valid_combinations.append((path[:], sum(values[j] for j in path)))
        return
    # Take item
    path.append(i)
    dfs(i + 1, w + weights[i], path)
    path.pop()
    # Skip item
    dfs(i + 1, w, path)
```



4. Coin Change
```python
class Solution:
    def coinChange(self, coins: List[int], amount: int) -> int:
        
        coins.sort()  # optional: can improve pruning in some variants

        from functools import lru_cache
        @lru_cache(None)

        def dfs(remain):
            if remain == 0:
                return 0
            if remain < 0:
                return float('inf')

            min_coins = float('inf')
            for coin in coins:
                min_coins = min(min_coins, dfs(remain - coin) + 1)
            return min_coins

        res = dfs(amount)
        return res if res != float('inf') else -1

```
5. Shopping Offers 
  ```python
  class Solution:
    def shoppingOffers(self, price: List[int], special: List[List[int]], needs: List[int]) -> int:
        
        n = len(price)

        from functools import lru_cache
        @lru_cache(None)

        def dfs(remain):
            # Base case: buy remaining items individually
            min_cost = sum(remain[i] * price[i] for i in range(n))

            # Try each special offer
            for s in special:
                new_remain = []
                for i in range(n):
                    if remain[i] < s[i]:
                        break
                    new_remain.append(remain[i] - s[i])
                else:
                    # All items in special are affordable
                    min_cost = min(min_cost, dfs(tuple(new_remain)) + s[-1])
            return min_cost

        return dfs(tuple(needs))
```
