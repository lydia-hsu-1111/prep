```python
def recursive_function(node):
    # Base case
    if node is None:
        return base_case_value
    
    # Recursive calls
    left_result = recursive_function(node.left)
    right_result = recursive_function(node.right)
    
    # Early exit condition (optional)
    if some_condition_based_on(left_result, right_result):
        return special_value_or_flag
    
    # Combine left, right and current node's value for result
    result = combine(left_result, right_result, node.val)
    
    return result
```


# Why post-order tree recursion is often trickier:
1. You need info from both children before deciding what to do at the current node.
This means you have to manage and combine multiple results — sometimes carefully handling nulls, edge cases, or multiple return values.

2. It’s “bottom-up” reasoning:
Unlike pre-order (root first) or in-order (mostly BSTs with sorted traversal), post-order forces you to think about solving smaller subproblems fully before you can solve the bigger one.

3. State aggregation and passing values upward:
Many advanced tree problems (max path sum, diameter, subtree computations, LCA variants) require you to compute partial results for subtrees and combine them correctly. The combination logic can get subtle.

4. You have to keep track of global state (e.g., max path length) separately because the answer might not be purely from one recursive call but from combining both subtrees at the current node.

# Tips to master post-order tree problems:
1. Draw the tree and label return values from left and right subtrees.
2. Clearly identify what your recursive function returns at each node.
3. Keep a global variable outside recursion for things like max values.
4. Write base cases first (null nodes).
5. Practice breaking down problems into “solve left subtree”, “solve right subtree”, “combine results” pattern.

# Examples to compare:
1. Check Balanced Tree
```python
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        def check(node):
            if not node:
                return 0
            
            left = check(node.left)
            if left is False:
                return False

            right = check(node.right)
            if right is False:
                return False

            if abs(left - right) > 1:
                return False

            return max(left, right) + 1

        return check(root) is not False
```
2. Lowest Common Ancestor
```python
class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        def dfs(node):
            if not node or node == p or node == q:
                return node

            left = dfs(node.left)
            right = dfs(node.right)

            if left and right:
                return node
            if left:
                return left
            if right:
                return right

            return None  # optional, for clarity

        return dfs(root)
```
