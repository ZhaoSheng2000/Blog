### 题目描述
102. 二叉树的层序遍历
给你二叉树的根节点 root ，返回其节点值的 层序遍历 。 （即逐层地，从左到右访问所有节点）。

 
示例 1：
![](https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg)

```
输入：root = [3,9,20,null,null,15,7]
输出：[[3],[9,20],[15,7]]
```
示例 2：
```
输入：root = [1]
输出：[[1]]
```
示例 3：
```
输入：root = []
输出：[]
```

### 解题思路

> 二叉树的层序遍历是一个解题模板啊！

直接上代码
```
var levelOrder = function(root) {
    let res =[];
    let queue = [root]; //辅助队列来推入每一层节点
    if(root === null) return res; //为空的特殊用例
    while(queue.length){ 只要这个队列还有节点，就一直搞他
        let curLevel = [];
        for(let i=0,len=queue.length;i<len;i++){ //每一层有好多个要遍历啊
            const node = queue.shift();//当前层的一个节点
            curLevel.push(node.val);
            node.left&&queue.push(node.left);//继续往这个数组里面推节点
            node.right&&queue.push(node.right);
        }
        res.push(curLevel)
    }
    return res;
};
```
**这个代码十分的关键啊！**
有好多题目否可以根据这个层序遍历稍微改动一下就可以得到结果了。

例如：

[107.二叉树的层序遍历 II ](https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii/)
这道题只需要将得到的每一层的节点反转一下再推入结果数组就好啦～
后面还有「二叉树的最大深度」，「二叉树的右视图」，我再单独搞好了

