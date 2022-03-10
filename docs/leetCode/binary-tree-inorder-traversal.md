
### 题目描述
94.二叉树的中序遍历

[leetcode链接](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

给定一个二叉树的根节点 ``root`` ，返回它的 **中序** 遍历。

示例 1：
![](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)
```
输入：root = [1,null,2,3]
输出：[1,3,2]
```
示例 2：
```
输入：root = []
输出：[]
```
示例 3：
```
输入：root = [1]
输出：[1]
```
示例 4：
![](https://assets.leetcode.com/uploads/2020/09/15/inorder_5.jpg)
```
输入：root = [1,2]
输出：[2,1]
```
示例 5：
[](https://assets.leetcode.com/uploads/2020/09/15/inorder_4.jpg)
```
输入：root = [1,null,2]
输出：[1,2]
```
---
### 解题
>「中序遍历」就是按照根结点在中间的顺序进行依次遍历。(我自己的理解)

我们要学会「举一反三」，那前序遍历后序遍历不是都懂了🤓

#### 直接开搞！

```
var inorderTraversal = function (root) {
    let res = [];
    const traverse = (root) => {
        if (root == null) return;
        traverse(root.left);
        res.push(root.val);
        traverse(root.right);
    }
    traverse(root);//调用一下
    return res
};
```

那么基于这个框架，

**前序遍历**不就是搞根结点的步骤放到最前面

**后序遍历**不就是把搞根结点的步骤放到最后面就成了。

基本操作，无需惊叹

打完收工～

