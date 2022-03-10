### 题目描述

[leetcode链接](https://leetcode-cn.com/problems/maximum-subarray/)

53.最大子数组和

给你一个整数数组 nums ，请你找出一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

子数组 是数组中的一个连续部分。

 

示例 1：
```
输入：nums = [-2,1,-3,4,-1,2,1,-5,4]
输出：6
解释：连续子数组 [4,-1,2,1] 的和最大，为 6 。
```
示例 2：
```
输入：nums = [1]
输出：1
```
示例 3：
```
输入：nums = [5,4,-1,7,8]
输出：23
```
---
### 解题

> 不要跟我讲什么框架，上来就是两层for循环，所有情况挑选最大，简单粗暴（我猜会超时）

直接上代码

```
var maxSubArray = function (nums) {
    let res = -Infinity;
    let sum = 0;
    for (let i = 0; i < nums.length; i++) {
        sum = 0; //第二层开始，要归零了

        for (let j = i; j < nums.length; j++) { // j = i很关键啊这波
            sum = sum + nums[j] //每次加完都有可能是最后取得最大值的结果
            res = Math.max(res, sum) //取一下res的值
        }
    }
    return res;
};
```


果然不出我所料，暴力破解是超时滴

![](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203101637867.png)

那么接下来就来搞一搞「贪心算法」

```
var maxSubArray = function (nums) {
    let res = - Infinity;
    let money = 0; //没错，贪心贪得就是money
    for (let i = 0; i < nums.length; i++) {
        money = money + nums[i];//开始圈钱  
        res = Math.max(res, money);

        if (money < 0) {
            money = 0; //负数了我就清零了，前面的也不圈了
        }
    }
    return res;
};
```

完美通过～

![](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203101645526.png)


贪心算法也不满足，要举一反三嘛,下面就要祭出我的好大哥「动态规划」

>动态规划就是缓存一堆数据的迭代（之前计算过的）结果，在下一次的时候直接用，来减少运算量。

简单理一下思路：
1. 我什么也没有:[]
2. 我有了a :[a],现在包含a的最大值是 a
3. 我有了b: [a] <-b 现在包含a,b的最大值是Math.max((包含a的最大值 + b), b自己)
4. 我有了c：[a,b] <-c 现在包含a,b,c的最大值是Math.max((包含b的最大值 + c), c自己)
5. ...
6. ...

总结起来就是：
``dp[i] =Math.max((dp[i-1]+nums[i]),nums[i])``

i表示包含了第几个元素（包含了新放进去的元素）、
dp[i]表示包含了第几个元素的最大值


那么我们就相当于有了
dp[1]:包含第1元素的最大值
dp[2]:包含第2元素的最大值
dp[3]:包含第3元素的最大值
......
dp[i]:包含第i元素的最大值

那么结果不就是在dp[i]里面挑选一个最大的吗？

思路搞清楚直接开干！

```
var maxSubArray = function (nums) {
    let dp = []; 
    dp[0] = nums[0];//题目中规定了数组中至少有一个元素
    let res = dp[0]; 

    for (let i = 1; i < nums.length; i++) {
        dp[i] = Math.max((dp[i - 1] + nums[i]), nums[i]);
        res = Math.max(res, dp[i]);
    }
    return res;
};
```
完美通过！

![](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203101721091.png)



