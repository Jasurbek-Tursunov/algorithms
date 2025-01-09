## [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal/)

- Time: ***O(n)***
- Memory: ***O(n)***

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func preorderTraversal(root *TreeNode) []int {
    if root == nil {
        return []int{}
    }
    
    result := append([]int{}, root.Val)
    
    resultLeft := preorderTraversal(root.Left)
    result = append(result, resultLeft...)
    
    resultRight := preorderTraversal(root.Right)
    result = append(result, resultRight...)
    
    return result
}
```



## [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

- Time: ***O(n)***
- Memory: ***O(n)***

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func inorderAdder(head *TreeNode, arr *[]int) {
    if head == nil {
        return
    }

    inorderAdder(head.Left, arr)
    *arr = append(*arr, head.Val)
    inorderAdder(head.Right, arr)
}

func inorderTraversal(root *TreeNode) []int {
    result := []int{}

    inorderAdder(root, &result)

    return result
}
```



## [145. Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal/)

- Time: ***O(n)***
- Memory: ***O(n)***

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func postorderAdder(node *TreeNode, arr *[]int) {
    if node == nil {
        return
    }

    postorderAdder(node.Left, arr)
    postorderAdder(node.Right, arr)
    *arr = append(*arr, node.Val)
}

func postorderTraversal(root *TreeNode) []int {
    result := []int{}

    postorderAdder(root, &result)

    return result
}
```



## [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

- Time: ***O(n)***
- Memory: ***O(n)***

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func preorderWithLevel(node *TreeNode, level int, arr*[][]int) {
    if node == nil {
        return
    }

    if level == len(*arr) {
        *arr = append(*arr, []int{})
    }

    (*arr)[level] = append((*arr)[level], node.Val)
    preorderWithLevel(node.Left, level + 1, arr)
    preorderWithLevel(node.Right, level + 1, arr)
}

func levelOrder(root *TreeNode) [][]int {
    result := [][]int{}

    preorderWithLevel(root, 0, &result)

    return result
}
```



## [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

- Time: ***O(n)***
- Memory: ***O(h)***

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func equal(left, right *TreeNode) bool {
    if left == nil || right == nil {
        return left == nil && right == nil
    }

    if left.Val != right.Val {
        return false
    }

    return equal(left.Left, right.Right) && equal(left.Right, right.Left)
}

func isSymmetric(root *TreeNode) bool {
    return root == nil || equal(root.Left, root.Right)
}
```



## [100. Same Tree](https://leetcode.com/problems/same-tree/)

- Time: ***O(n)***
- Memory: ***O(h)***

```golang
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func isSameTree(p *TreeNode, q *TreeNode) bool {
    if p == nil || q == nil {
        return p == nil && q == nil
    }

    if p.Val != q.Val {
        return false
    }

    return isSameTree(p.Left, q.Left) && isSameTree(p.Right, q.Right)
}
```
