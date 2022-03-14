### 题目描述

112.路径总和
[链接](https://leetcode-cn.com/problems/path-sum/)
给你二叉树的根节点 root 和一个表示目标和的整数 targetSum 。判断该树中是否存在 根节点到叶子节点 的路径，这条路径上所有节点值相加等于目标和 targetSum 。如果存在，返回 true ；否则，返回 false 。

叶子节点 是指没有子节点的节点。

 

示例 1：
![](https://assets.leetcode.com/uploads/2021/01/18/pathsum1.jpg)
```
输入：root = [5,4,8,11,null,13,4,7,2,null,null,null,1], targetSum = 22
输出：true
解释：等于目标和的根节点到叶节点路径如上图所示。
```
示例 2：
```

输入：root = [1,2,3], targetSum = 5
输出：false
解释：树中存在两条根节点到叶子节点的路径：
(1 --> 2): 和为 3
(1 --> 3): 和为 4
不存在 sum = 5 的根节点到叶子节点的路径。
```
示例 3：
```
输入：root = [], targetSum = 0
输出：false
解释：由于树是空的，所以不存在根节点到叶子节点的路径。
```

### 解题
>简单的递归

```
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} targetSum
 * @return {boolean}
 */
var hasPathSum = function(root, targetSum) {
    if(root === null) return false;
    if(root.left===null && root.right === null){
        return (targetSum - root.val )=== 0
    }
    let left =hasPathSum(root.left,targetSum - root.val) 
    let right = hasPathSum(root.right,targetSum - root.val) 
    return left || right
};
```

写递归的思路其实和人眼观察的思路是一样的

首先盯着一小部分范围的数据写，然后扩大至全局，注意调整参数就ok了。