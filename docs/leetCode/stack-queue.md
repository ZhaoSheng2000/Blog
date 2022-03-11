### 题目描述
232.用栈实现队列 
    
[leetcode](https://leetcode-cn.com/problems/implement-queue-using-stacks/)

请你仅使用两个栈实现先入先出队列。队列应当支持一般队列支持的所有操作（push、pop、peek、empty）：

实现 MyQueue 类：

- void push(int x) 将元素 x 推到队列的末尾
- int pop() 从队列的开头移除并返回元素
- int peek() 返回队列开头的元素
- boolean empty() 如果队列为空，返回 true ；否则，返回 false


说明：

- 你 只能 使用标准的栈操作 —— 也就是只有 push to top, peek/pop from top, size, 和 is empty 操作是合法的。
- 你所使用的语言也许不支持栈。你可以使用 list 或者 deque（双端队列）来模拟一个栈，只要是标准的栈操作即可。
 

示例 1：
```
输入：
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
输出：
[null, null, null, 1, 1, false]
```
解释：
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false

### 解题
> 栈和队列就不用多说了

针对js，栈操作只有：arr.push(); arr.pop();也就是需要用这两个操作来模拟要求的三种方法。``push(),pop(),peek()``

只用栈的操作来实现队列的功能，仅仅靠一个栈是不行的，所以还需要一个辅助栈
也就是一个「输入栈」，一个「输出栈」

```
// 使用两个数组的栈方法（push, pop） 实现队列
/**
* Initialize your data structure here.
*/
var MyQueue = function() {
   this.stack1 = [];
   this.stack2 = [];
};

/**
* Push element x to the back of queue. 
* @param {number} x
* @return {void}
*/
MyQueue.prototype.push = function(x) {
   this.stack1.push(x);
};

/**
* Removes the element from in front of queue and returns that element.
* @return {number}
*/
MyQueue.prototype.pop = function() {
   const size = this.stack2.length;
   if(size) {
       return this.stack2.pop();
   }
   while(this.stack1.length) {
       this.stack2.push(this.stack1.pop());
   }
   return this.stack2.pop();
};

/**
* Get the front element.
* @return {number}
*/
MyQueue.prototype.peek = function() {
   const x = this.pop();
   this.stack2.push(x);
   return x;
};

/**
* Returns whether the queue is empty.
* @return {boolean}
*/
MyQueue.prototype.empty = function() {
   return !this.stack1.length && !this.stack2.length
};

```

在push数据的时候，只要数据放进输入栈就好，但在pop的时候，操作就复杂一些，输出栈如果为空，就把进栈数据全部导入进来（注意是全部导入），再从出栈弹出数据，如果输出栈不为空，则直接从出栈弹出数据就可以了。

如果输入栈和输出栈都为空的话，说明模拟的队列为空了。

提交，通过～
![](https://raw.githubusercontent.com/ZhaoSheng2000/imgBed/main/img/202203111549940.png)

这道题实现起来其实也不难，甚至peek都是调用的``pop()``方法，主要是需要了解栈和队列工作的原理和处理元素的方式。

那么举一反三，「用队列模拟栈」也是一样的道理。
