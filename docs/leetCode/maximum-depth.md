### 题目描述

104. 二叉树的最大深度 https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/
     
给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

示例：
给定二叉树 ``[3,9,20,null,null,15,7]``，
```
    3
   / \
  9  20
    /  \
   15   7
```
返回它的最大深度 3 。

### 题解

>今天又来搞二叉树相关的题目了

这个题首先想到的就是层序遍历，最大深度不就是他的层数吗？

也可以使用递归，递归敲的代码少啊！
先来递归
```
var maxDepth = function(root) {
    if(!root) return 0;//如果当前节点没有就返回0
    //如果有节点就深度+1再加上它 爸爸，妈妈的最大深度
    //再加上爷爷 奶奶,爷爷 奶奶又可以通过爸爸妈妈递归调用取得，妙啊
    return 1 + Math.max(maxDepth(root.left),maxDepth(root.right))
};
```

