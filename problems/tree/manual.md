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
