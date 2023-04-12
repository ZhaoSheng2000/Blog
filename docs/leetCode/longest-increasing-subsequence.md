### 题目描述

300.最长递增子序列

[leetcode](https://leetcode-cn.com/problems/longest-increasing-subsequence/)

给你一个整数数组 ``nums`` ，找到其中最长严格递增子序列的长度。

**子序列** 是由数组派生而来的序列，删除（或不删除）数组中的元素而不改变其余元素的顺序。例如，``[3,6,2,7]`` 是数组 ``[0,3,1,6,2,2,7]`` 的子序列。

 
示例 1：
```
输入：nums = [10,9,2,5,3,7,101,18]
输出：4
解释：最长递增子序列是 [2,3,7,101]，因此长度为 4 。
```
示例 2：
```
输入：nums = [0,1,0,3,2,3]
输出：4
```
示例 3：
```
输入：nums = [7,7,7,7,7,7,7]
输出：1
```

### 解题
> 这道题算动态规划入门版本,计划刷一系列这样的动规来过过瘾🤓

```
var lengthOfLIS = function(nums) {
    let res = 1;
    let dp = Array(nums.length).fill(1);

    for(let i = 1 ;i<nums.length;i++){
        for(let j = 0;j<i;j++){
            if(nums[i]>nums[j]){
                dp[i] = Math.max(dp[i],dp[j]+1)
            }
        }
        res = Math.max(dp[i],res)
    }
    return res
};
```
动态规划的核心思想：**数学归纳**



- 先定义dp[i]代表的含义：``dp[i]`` 表示以 ``nums[i]`` 这个数结尾的最长递增子序列的长度。为什么这样定义呢？看到的题目多了就能看出来这种题目的套路了，就几种dp的定义的方法👌
- base case:``dp[i]`` 初始值为 1，因为以`` nums[i]`` 结尾的最长递增子序列起码要包含它自己.
- 列举前几项，得出结果是``dp[]``中的最大值
  ![dp](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203132125976.png)
- 状态转移方程：「数学归纳」的思想，根据刚才我们对 dp 数组的定义，现在想求 ``dp[5]`` 的值，也就是想求以 ``nums[5]`` 为结尾的最长递增子序列。 既然是递增子序列，我们只要找到前面那些结尾比当前值 ``3``小的子序列，然后把``3`` 接到最后，就可以形成一个新的递增子序列，而且这个新的子序列长度加一。可能形成很多种新的子序列，但是我们只选择最长的那一个,把最长子序列的长度作为 dp[5] 的值即可.
  ```for (int j = 0; j < i; j++) {
    if (nums[i] > nums[j]) 
        dp[i] = Math.max(dp[i], dp[j] + 1);
    }
    ```
- 最后列出完整代码
    ```
    var lengthOfLIS = function(nums) {
    let res = 1;
    let dp = Array(nums.length).fill(1);

    for(let i = 1 ;i<nums.length;i++){
        for(let j = 0;j<i;j++){
            if(nums[i]>nums[j]){
                dp[i] = Math.max(dp[i],dp[j]+1)
            }
        }
        res = Math.max(dp[i],res)
    }
    return res
    };  
    ```

    至此，这道题就解决了，时间复杂度 O(N^2)。下面总结一下如何找到动态规划的状态转移关系。
### 总结


1、明确 dp 数组所存数据的含义。这一步对于任何动态规划问题都很重要，如果不得当或者不够清晰，会阻碍之后的步骤。

2、根据 dp 数组的定义，运用数学归纳法的思想，假设 ``dp[0...i-1]`` 都已知，想办法求出`` dp[i]``，一旦这一步完成，整个题目基本就解决了。

但如果无法完成这一步，很可能就是 ``dp``数组的定义不够恰当，需要重新定义 dp 数组的含义；或者可能是 ``dp`` 数组存储的信息还不够，不足以推出下一步的答案，需要把 dp 数组扩大成二维数组甚至三维数组。