# LeetCode Famous Algorithms Cheat Sheet with Templates

## 1. Floyd's Cycle Detection (Tortoise & Hare)
```python
def hasCycle(head):
    slow = fast = head
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

## 2. Dutch National Flag (3-Way Partitioning)
```python
def sortColors(nums):
    low, mid, high = 0, 0, len(nums) - 1
    while mid <= high:
        if nums[mid] == 0:
            nums[low], nums[mid] = nums[mid], nums[low]
            low += 1
            mid += 1
        elif nums[mid] == 1:
            mid += 1
        else:
            nums[mid], nums[high] = nums[high], nums[mid]
            high -= 1
```

## 3. Binary Search on Answer
```python
def binarySearch(low, high, is_feasible):
    while low < high:
        mid = (low + high) // 2
        if is_feasible(mid):
            high = mid
        else:
            low = mid + 1
    return low
```

## 4. Monotonic Stack
```python
def nextGreaterElements(nums):
    res = [-1] * len(nums)
    stack = []
    for i in range(len(nums)):
        while stack and nums[stack[-1]] < nums[i]:
            res[stack.pop()] = nums[i]
        stack.append(i)
    return res
```

## 5. Prefix Sum + Hashing
```python
def subarraySum(nums, k):
    count = 0
    total = 0
    prefix = {0: 1}
    for num in nums:
        total += num
        count += prefix.get(total - k, 0)
        prefix[total] = prefix.get(total, 0) + 1
    return count
```

## 6. Sliding Window / Two Pointers
```python
def lengthOfLongestSubstring(s):
    seen = set()
    l = res = 0
    for r in range(len(s)):
        while s[r] in seen:
            seen.remove(s[l])
            l += 1
        seen.add(s[r])
        res = max(res, r - l + 1)
    return res
```

## 7. Topological Sort (Kahn's Algorithm)
```python
from collections import deque, defaultdict

def topoSort(n, edges):
    indegree = [0] * n
    graph = defaultdict(list)
    for u, v in edges:
        graph[u].append(v)
        indegree[v] += 1
    queue = deque([i for i in range(n) if indegree[i] == 0])
    res = []
    while queue:
        node = queue.popleft()
        res.append(node)
        for nei in graph[node]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                queue.append(nei)
    return res if len(res) == n else []
```

## 8. Reservoir Sampling
```python
import random

def reservoir_sample(iterator, k):
    reservoir = []
    for i, item in enumerate(iterator):
        if i < k:
            reservoir.append(item)
        else:
            j = random.randint(0, i)
            if j < k:
                reservoir[j] = item
    return reservoir
```

## 9. Moore's Voting Algorithm
```python
def majorityElement(nums):
    count = 0
    candidate = None
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
    return candidate
```

## 10. Sweep Line / Event Sorting
```python
def minMeetingRooms(intervals):
    starts = sorted([i[0] for i in intervals])
    ends = sorted([i[1] for i in intervals])
    s = e = rooms = 0
    while s < len(intervals):
        if starts[s] < ends[e]:
            rooms += 1
            s += 1
        else:
            e += 1
            s += 1
    return rooms
```

## 11. Kadane's Algorithm
```python
def maxSubArray(nums):
    max_sum = curr = nums[0]
    for n in nums[1:]:
        curr = max(n, curr + n)
        max_sum = max(max_sum, curr)
    return max_sum
```

## 12. Manacher's Algorithm
```python
def manachers(s):
    A = '@#' + '#'.join(s) + '#$'
    Z = [0] * len(A)
    center = right = 0
    for i in range(1, len(A) - 1):
        if i < right:
            Z[i] = min(right - i, Z[2 * center - i])
        while A[i + Z[i] + 1] == A[i - Z[i] - 1]:
            Z[i] += 1
        if i + Z[i] > right:
            center, right = i, i + Z[i]
    return max(Z)
```

## 13. Dijkstra's Algorithm (Shortest Path)
```python
import heapq
from collections import defaultdict

def dijkstra(n, graph, start):
    dist = [float('inf')] * n
    dist[start] = 0
    minHeap = [(0, start)]
    while minHeap:
        d, u = heapq.heappop(minHeap)
        if d > dist[u]: continue
        for v, w in graph[u]:
            if dist[u] + w < dist[v]:
                dist[v] = dist[u] + w
                heapq.heappush(minHeap, (dist[v], v))
    return dist
```
