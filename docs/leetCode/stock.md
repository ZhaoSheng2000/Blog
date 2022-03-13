### 题目描述

leetcode链接：[121.买卖股票的最佳时机](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)
    
给定一个数组 prices ，它的第 i 个元素 prices[i] 表示一支给定股票第 i 天的价格。

你只能选择 某一天 买入这只股票，并选择在 未来的某一个不同的日子 卖出该股票。设计一个算法来计算你所能获取的最大利润。

返回你可以从这笔交易中获取的最大利润。如果你不能获取任何利润，返回 0 。

 

示例 1：
```
输入：[7,1,5,3,6,4]
输出：5
解释：在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格；同时，你不能在买入前卖出股票。
```
示例 2：
```
输入：prices = [7,6,4,3,1]
输出：0
解释：在这种情况下, 没有交易完成, 所以最大利润为 0。
```

---
### 解题
>上来就是一个暴力算法！
```
var maxProfit = function(prices){
    let max = 0;
    for(let i = 0; i < prices.length; i++){
        for(let j = i;j < prices.length; j++){
            const buy = prices[i]; //买入价格
            const sell = prices[j]; //卖出价格
            max = Math.max(max,sell - buy); //两者相减取其最大
        }
    }
    return max; 
}
```
打完提交～

上来就是一个超时啊🤮
![](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203090956544.png)
![](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203090957779.png)

这就很恶心啊，不要担心，买卖只有一次，那我直接买入今天为止股票的最低点，未来的最高点，那剩下的不就是最大利润了吗👏

```
var maxProfit = function(prices){
    if(!prices.length) return 0;
    let min = prices[0];
    let max = 0;
    for(let p of prices){
        min = Math.min(p,min); //今天为止股票的最低点
        const  curProfit = p-min; //今天卖了能赚多少钱
        max = Math.max(curProfit,max) //和之前赚的钱取最大值
                    //（今天卖赚钱多？之前某一天卖的赚钱多）
    }
    return max;
}
```
**还写什么代码，我就是下一个巴菲特啊！**