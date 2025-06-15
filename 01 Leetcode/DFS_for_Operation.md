## DFS for Operational Purposes

### Cycle Detection (Directed Graph)
```python
from collections import defaultdict

def has_cycle(n, edges):
    # Build adjacency list
    graph = defaultdict(list)
    for u, v in edges:
        graph[u].append(v)

    visited = [0] * n  # 0 = unvisited, 1 = visiting, 2 = visited

    def dfs(node):
        if visited[node] == 1:
            return True  # cycle detected
        if visited[node] == 2:
            return False  # already processed

        visited[node] = 1  # mark as visiting
        for neighbor in graph[node]:
            if dfs(neighbor):
                return True
        visited[node] = 2  # mark as visited
        return False

    for i in range(n):
        if visited[i] == 0:
            if dfs(i):
                return True
    return False
```

### Cycle Detection (Undirected Graph)
```python
from collections import defaultdict

def has_cycle(n, edges):
    graph = defaultdict(list)
    for u, v in edges:
        graph[u].append(v)
        graph[v].append(u)  # undirected graph → add both directions

    visited = [False] * n

    def dfs(node, parent):
        visited[node] = True
        for neighbor in graph[node]:
            if not visited[neighbor]:
                if dfs(neighbor, node):
                    return True
            elif neighbor != parent:
                return True  # Found a back edge (cycle)
        return False

    for i in range(n):
        if not visited[i]:
            if dfs(i, -1):
                return True
    return False
```
### Clone Tree
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def clone_tree(root):
    if not root:
        return None

    # Create a new node with the same value
    new_node = TreeNode(root.val)
    
    # Recursively clone left and right subtrees
    new_node.left = clone_tree(root.left)
    new_node.right = clone_tree(root.right)

    return new_node
```

### Clone Graph
```python
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []

def cloneGraph(node: 'Node') -> 'Node':
    if not node:
        return None
    
    visited = {}

    def dfs(n):
        if n in visited:
            return visited[n]
        
        # Clone the node
        clone = Node(n.val)
        visited[n] = clone
        
        # Clone all neighbors recursively
        for nei in n.neighbors:
            clone.neighbors.append(dfs(nei))
        
        return clone
    
    return dfs(node)
```

### Reverse Linked List
1. reverse as it unwinds back up (classic recursive backtracking)
```python
# Definition for singly-linked list.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def reverseList(head: ListNode) -> ListNode:
    # Base case: empty list or single node
    if not head or not head.next:
        return head
    
    # Recursively reverse the rest of the list
    new_head = reverseList(head.next)
    
    # Put current node after the reversed list
    head.next.next = head
    head.next = None
    
    return new_head
```
2. reverse as it descends
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        def dfs(pre, curr):
            if not curr:
                return pre
            next_node = curr.next
            curr.next = pre
            new_head = dfs(curr, next_node)
            return new_head
        return dfs(None,head)
```
