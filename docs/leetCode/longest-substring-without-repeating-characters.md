### 题目描述

3.无重复字符的最长子串
[链接](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
给定一个字符串 ``s`` ，请你找出其中不含有重复字符的 **最长子串** 的长度。
 

示例 1:
```
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```
示例 2:
```
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```
示例 3:
```
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
 ```

### 解题
> 可以借助Map来开辟新的空间来记录下标

```
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let res = 0;
    let left = 0; //指针的下标
    let map = new Map();
    for(let i = 0; i< s.length;i++){
        if(map.has(s[i])&&map.get(s[i])>=left){ //如果表中有,指针后移
          left = map.get(s[i])+1;
        }
        map.set(s[i],i)
        res = Math.max(res,i-left+1);
    }
    return res;
};
```