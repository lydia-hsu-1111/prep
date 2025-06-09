## Principles:
1. Pre-order is often used for building or serialization, path finding problems.
2. In-order is classic for BST related problems where sorted order matters.
3. Post-order is essential for aggregating subtree information and combining results (e.g., max path sum, diameter).

## Examples:
### Pre-order (Root → Left → Right)
* Binary Tree Paths (LC257)
* Path Sum (LC112)
* Path Sum II (LC113)
* Construct Binary Tree from Preorder and Inorder Traversal (LC105) — technically mixed but root discovery first
* Serialize and Deserialize Binary Tree (LC297) (serialization often pre-order)
* Invert Binary Tree (LC226)
* Flatten Binary Tree to Linked List (LC114)
* Symmetric Tree (LC101) — pre-order symmetry check
* Sum Root to Leaf Numbers (LC129)
* Find Bottom Left Tree Value (LC513) (can be pre-order with depth tracking)
* Recover Binary Search Tree (LC99) (pre-order-ish for node swapping)
* Maximum Depth of Binary Tree (LC104) (can be done pre-order)

### In-order (Left → Root → Right)
* Validate Binary Search Tree (LC98)
* Recover Binary Search Tree (LC99) (in-order traversal to detect swapped nodes)
* Kth Smallest Element in a BST (LC230)
* Binary Search Tree Iterator (LC173) (uses in-order traversal)
* Convert BST to Greater Tree (LC538) (reverse in-order)
* Convert Sorted Array to BST (LC108) — indirectly uses in-order logic
* Convert Sorted List to BST (LC109) (similar)
* Closest Binary Search Tree Value (LC270)
* Lowest Common Ancestor of a BST (LC235) (leverages BST property which can be in-order related)
* Inorder Successor in BST (LC285)

### Post-order (Left → Right → Root)
* Maximum Depth of Binary Tree (LC104) (also post-order)
* Balanced Binary Tree (LC110)
* Diameter of Binary Tree (LC543)
* Binary Tree Maximum Path Sum (LC124)
* Lowest Common Ancestor of a Binary Tree (LC236)
* Subtree of Another Tree (LC572)
* Count Univalue Subtrees (LC250)
* Delete Node in a BST (LC450)
* Flatten Binary Tree to Linked List (LC114) (also can be post-order)
* Sum of Left Leaves (LC404)
* Construct Binary Tree from Inorder and Postorder Traversal (LC106)
* Serialize and Deserialize Binary Tree (LC297) (deserialization often post-order)
* Path Sum III (LC437) (usually post-order with prefix sums)
