### 国际化电商 前端2面
基本数据类型
class生命周期
class component转化为function component
diff算法
事件循环代码题
多个链表顺序合并
时间复杂度

### 字节面经|飞书前端暑期实习一面凉经（复盘）
作者：我头发茂盛
链接：https://www.nowcoder.com/discuss/864975?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647609638072
来源：牛客网

自我介绍，问有没有了解过服务端（说了了解一点）
1. 问项目登录注册实现过程，用到了cookie，所以一直在问cookie，大坑
2. cookie的属性有哪些？（所有都说，然后一一列举都有什么作用）
3.  如何预防xss/csrf攻击？（开启httponly、samesite属性设置成lax，对用户输入内容进行过滤）
4. samesite属性说一下？
5. samesite属性的lax值？
6. domain属性说一下 ？
7. 如何配置跨域允许携带cookie？（withcredentials设置为true）
8. 子域也能携带cookie吗？（指定了domain就可以携带）
9. 行内元素设置padding有什么效果？ （有左右边距，没有上下边距）
10. 行内块元素之间出现间隙的原因以及如何解决？（给出了具体案例，当时没看出来）
11 transfrom做动画和left做动画那个性能更高，为什么？(transform更高)
12. html多个空白字符合并成一个，为什么会这么做？（这里不太懂，有没有懂的大佬解释一下）
13. absolute相对于谁进行定位？( fixed、relative)
14. 说一些http状态码？
15. 301和302的区别？
16. 如何获取重定向后的地址？
17. 401和402的区别？
18. 前端如何判断服务端的具体错误（这里没太懂什么意思，捕获错误判断error里面的msg？）
算法题
1. 版本对比
var compareVersion = function (version1, version2) {
    let v1 = version1.split("."), v2 = version2.split(".")
    let n = v1.length, m = v2.length
    let i = 0, j = 0
    while (i < n || j < m) {
        let a = 0, b = 0
        if (i < n) a = parseInt(v1[i++])
        if (j < m) b = parseInt(v2[j++])
        if (a != b) return a > b ? 1 : -1
    }
    return 0
};

1. 宇符串格式化 
function format(s) {
    let res = "", k = 0
    for (let i = s.length - 1; i >= 0; i--) {
      res = s[i] + res
      k++
      if (k == 3) {
        res = "," + res
        k = 0
      }
    }
    return res[0] == ',' ? res.slice(1) : res;
  }
 
 
  console.log(format("23456789"))
  // 显示效果： "23,456,789"

反问环节
1.问技术栈

2.问学习方法


### 字节跳动校招，抖音电商前端，一二面面经

作者：青春沙雕少年
链接：https://www.nowcoder.com/discuss/864840?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647609638072
来源：牛客网

3月3日 一面（50min）
原本定于2.25一面的，但是面试官临时有事。。。拖到了3.3

自我介绍
在学校参加了一些项目和比赛，然后有一段实习经历，去年九月系统学习前端
学习渠道：入门是同学带，系统学习是红宝书，b站，然后踩坑就找掘金思否CSDN

1.基本数据类型
多说了symbol和bigint，面试官稍微问了下用过没，是干啥的，symobol用过，bigint只在教程里看见过

2.一个原型链的输出题
function Ctor(x){
  this.x=x
}
Ctor.prototype.x='12345'
const a=new Ctor(4)
a.x=undefined
console.log(a.x)//这里我答的12345，以为赋值undefined会去原型链上找hhhh，实际上赋值啥就是啥（undefined）
const b=new Ctor(5)
delete b.x
console.log(b.x)//这里是12345
3.事件循环，输出题
//1 3 4 5 2
new Promise(resolve=>{
  console.log(1)
  setTimeout(()=>{
    resolve()
  },0)
})
.then(()=>{
  console.log(4)
})
.then(()=>{
  console.log(5)
})
setTimeout(() => {
  console.log(2)
}, 0);
console.log(3)
4.web安全
xss，csrf，http劫持，dns劫持，ddos
仔细问了一下csrf的攻击原理

5.跨域的解决方法
简单说了下跨域的产生，和同源策略的限制
父子域名location.domain再设置端口号，代理服务器，websocket，cors，jsonp，cors问了怎么携带cookie，没答上来（withcredential）

6.ssl加密的过程
追问非对称加密加密的是什么（会话秘钥）

7.动画效果方案
transition（嘴瓢说了transiform），animation，requestAnimationFrame

8.手写一个深拷贝
自己没考虑数组，而且没用hasOwnProperty，复制了原型上的属性

9.为Array实现一个getReader
题目上是TS写法，然后我不会，就实现了一个函数返回一个Reader

10.反问
问了问哪里答得不好需要加强
学习建议

3月15日 二面（1h）
原本是3.11的，结果面试官也有事，然后跟hr小姐姐又换了好几个面试官都没空，最后又定到3.15

自我介绍
跟一面差不多的自我介绍
问了问实习项目中怎么解决eCharts没法用相对单位的问题

1.js的类型检测
回答了typeof instanceof constructor Object.prototype.toString().call()
追问了一下为啥要用Objcet原型上的toString，慌神了直接胡言乱语说不用原型找不到hhhh（实际上是别的toSrring经常被重写）

2.如何理解js动态类型，有什么优缺点
声明时类型不固定，可以修改，不用调用各种类型转换的函数，编码灵活但容易出错
又追问了一下js数组的内存分配，我这里猜测和c++数组动态内存一样动态分配，不够就翻倍之类的

3.判断this
//一开始被绕进去了，面试官提醒了一下，我重头开始分析，后来对了
var length=10;
function fn(){
  return this.length+1
};
var obj={
  length:5,
  test1(){
    return fn()
  }
}
console.log(obj.test1())//11
obj.test2=fn
console.log(obj.test1()===obj.test2())//11===6,false
4.new的原理，过程
这里我直接给面试官手写了一个

5.js代码在V8中怎么执行的
这里直接问蒙了，啥也不会啊hhhh，如实和面试官说了不会，但说了一下自己的看法，分为编译过程和运行过程
追问这两个过程干了些什么，回答了编译期有语法检查之类的

6.从url到页面呈现经历了那些过程
找缓存-dns解析-tcp链接-http请求-页面渲染
追问了dns解析的过程（递归和迭代）和页面渲染的过程（css，html同步解析，遇到js就请求执行）
再追问js阻塞怎么办（script写在body后面，async，defer）

7.事件传播
先捕获再冒泡，addEventLisener的第三个参数是干什么的（决定事件在哪个阶段执行，true是捕获，false冒泡），这个属性有没有改变事件传播的顺序（只是决定事件在哪执行，没有改变事件传播的顺序）

8.浏览器存储和调用它们的api
localStorage，SessionStorage，Cookie

9.vue解决了什么问题
不用操作dom，组件化
追问vue的响应式（Object.defineProperty）
然后又问了vue怎么做的依赖收集（不清楚）

10.webpack解决了什么问题
回答了less sass转css，babel转es5，热更新，混淆压缩
问了less-loader，css-loader和style-loader分别的作用，这里如实说了不清楚，但自己认为less-loader是把less转css，css-loader是为了解决css的模块化，样式隔离，style-loader真不知道

11.js的模块化了解多少
用过commonjs的require和es6的import

12.flex:1效果是什么
先回大了flex:1是三个属性的简写，然后回答了效果

13.box-sizing干什么的（盒模型）
14.并发和并行的区别（不知道，说了句废话，面试官说我说了等于没说，哈哈哈哈）
15.线程和进程的联系和区别，这里回答的比较详细
追问了线程间通信的方式（消息队列，共享内存，信号量）
然后又追问了一个进程的内存空间里会存些什么（运行时的状态，信号量）

16.tcp为什么三次握手
说话已经开始结巴了，一开始说了一点没说清楚，；捋了捋说清楚了，四次会造成资源浪费，两次无法确定

17.对称和非对称加密的优缺点
回答了安全和速度
追问浏览器和服务器加密算法谁更快（不知道）

18.V8垃圾回收
（自己对V8了解确实不够呀）
问了垃圾回收的时机，回答内存不够就运行
追问了新旧GC的区别，回答不清楚区别，但知道旧GC的原理和缺点，猜测新GC应该一定程度上有所解决
追问谁执行的更频繁（我回答老的不如新的，得多清理几次，没想到错了hhhhh）

19.算法题-括号生成，我用动态规划写的，力扣上有
20.反问
问了问哪里答得不好
哪里需要加强（并行并发，还说V8不感兴趣没关系，面试官人真的挺好的，还跟我讲了一些业务上的问题）
学习建议
直接问过没过，面试官笑嘻嘻跟我说，不能讲，我觉得还不错，你自己体会
后来等了会hr就跟我说过了



### 字节——飞书 暑期实习web前端一面面经
作者：宋硕
链接：https://www.nowcoder.com/discuss/864396?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647609638072
来源：牛客网

1.自我介绍
2.学过什么专业课
3.栈和队列的区别？
我回答了三点。先进先出、遍历、速度队列更快
4.用两个栈实现队列。简单说了一下思路
5.进程间通信的方式?说了大概四五种。
6.共享内存的优缺点？我脑子卡壳了，没答上来，事后想想可能是优点节约空间操作方便，缺点就是多个进程同时使用的时候会拥挤
7.八种排序简述一下？冒泡、快速、归并、希尔、堆、之类的反正都说了，说了大概思路和怎么实现的
8.手写快速排序。限时10分钟，
9.设计模式有没有了解？简单说一下？我说了两种，实际上不止两种，其他的没了解过
10.vue父子组件间的通信方式？我说了三种。
11.我有什么想问的?

过程一小时，面试官小哥哥很好的，就是我比较紧张，脑子总是卡壳，磕磕巴巴的，不过也算勉强过了。



### 字节暑期实习 
作者：吃饭吃饭
链接：https://www.nowcoder.com/discuss/864121?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647610455653
来源：牛客网

字节（已offer）
一面
为什么算法转前端

谈谈项目中遇到的难点

说说虚拟dom

React diff算法，为什么快，传统diff算法复杂度是多少

谈谈浏览器缓存

OSI七层模型，TCP/IP五层模型

TCP三次握手，四次挥手

判断数组的方式

进程和线程的区别

浏览器中一个页面是一个进程还是一个线程，某个页面崩溃后会影响整个进程吗？

css手写题：等腰三角形

js手写题：leetcode 414. 第三大的数

二面
项目相关

讲一下https

网络协议为什么要分层

TCP拥塞控制，有什么缺点

进程间通信

处理机调度算法

js闭包讲一下

手写节流函数

手写一个工具函数：输入array或object，判断类型后遍历，并执行回调

三面
介绍一下原型链

谈一谈事件循环

说一下http的状态码

js中能表示的最大整数是多少，为什么

介绍一下React

你知道哪些设计模式

说一下快速排序，有哪些应用场景

算法题：leetcode  5. 最长回文子串
hr面
自我介绍

最近遇到的困难与挑战，你是怎么解决的

实习打算去哪个城市，为什么选杭州

### 字节抖音前端实习
作者：西行寺悟空
链接：https://www.nowcoder.com/discuss/861304?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647610455653
来源：牛客网

背景简述
本人23届CS弱相关专业，自学前端两个月，做过微信小程序的全栈开发项目，简历里写的技术栈是三大件+node+vue，除此之外无开发岗实习经历。当时是有学长给我了部门定向内推，日常实习，整体过程还算挺顺利的，觉得题目也相对基础。

面试问题
一面（约40min
介绍项目

jwt在项目中的具体实现，必要性？为什么不用微信API的鉴权？（答官方文档建议开发者自定登录态）

tcp与udp区别？应用场景？

get与post区别，应用场景？在项目中的使用？

http缓存控制，协商缓存？

https如何保证安全的？加密方式？公私钥交换过程？

跨域是什么？产生条件？在微信小程序中的运用？解决了什么？

jsonp有了解过吗？（答没有什么了解，之前看到跨域解决方案的时候有看到过对比，没有深入了解，熟悉的是cors和nginx反向代理。然后也没有追问下去了）

看输出，解释原因

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
// 1.局部作用域与全局作用域
let val = 1;
function foo() {
  console.log(val);
}
function bar() {
  let val = 2;
  foo();
}
bar();
 
// 2.this指向
window.name = 'ByteDance';
function A() {
  this.name = 123;
}
A.prototype.getA = function () {
  return this.name + 1;
};
let a = new A();
let funcA = a.getA;
console.log(funcA());
// 解释完上面答下面这种情况
console.log(a.getA());
 
// 3.this指向(call)
const obj = {
  birth: 1990,
  getAge(year) {
    let fn = y => y - this.birth;
    return fn.call({ birth: 2000 }, year);
  },
};
console.log(obj.getAge(2020));
 
// 4.执行顺序
async function async1() {
  console.log('async1 start');
  await async2();
  console.log('async1 end');
}
async function async2() {
  console.log('async2');
}
console.log('script start');
setTimeout(() => {
  console.log('setTimeout');
}, 0);
async1();
new Promise(function (resolve) {
  console.log('promise1');
  resolve();
}).then(function () {
  console.log('promise2');
});
console.log('script end');
算法：栈模拟队列 剑指 Offer 09. 用两个栈实现队列 - 力扣（LeetCode） (leetcode-cn.com)
二面（约70min
介绍项目，看项目后端中某个具体功能的具体代码（图片上传与处理）

实习经历？（简历上写的hr岗怎么就整开发了呢？噢，原来是用python编写脚本、使用文档，提升部门某项重复性耗时工作的工作效率）

浏览器不同标签页面通信？同源、跨域情况下？（可能我一直都没答到点子上，一直让我说有没有其他的方案，说了好几个能想到的，包括storage api,server侧配合websocket甚至外部应用程序

localStorage，sessionStorage区别？

css实现三角形！（我答的transform: rotate(45deg)然后在父元素overflow: hidden，插问了rotate的旋转中心怎么确定。总之是没答到正解border的点子上）

css position属性有哪些？区别是什么？详细说说fixed的定位方式？

看输出，解释原因

1
2
3
4
5
6
7
8
9
//1也是关于this的，还有闭包，和一面差不多
 
//2. 作用域？变量提升？
for(var i=0;i<5;i++){
  setTimeout(()=>{
    console.log(i);
  },0)
}
//3也是关于event loop的，和一面的执行顺序差不多，让具体解释了一下宏任务和微任务
算法：查找json中的children路径
现有如下json（简化为对象），已知每个节点id唯一，编写findNode(id)，返回路径，如findNode(5) 输出 1->4->5
（直接DFS就行，当时一下没想好回溯写了半天没写对，面试结束后两分钟搞定了）

1
2
3
4
5
6
7
8
9
10
11
12
13
14
{
  id: 1,
  children: [
    { id: 2, children: [{ id: 3, children: [] }] },
    {
      id: 4,
      children: [
        { id: 5, children: [] },
        { id: 6, children: [] },
      ],
    },
    { id: 7, children: [] },
  ],
};
算法：合并两个有序数组88. 合并两个有序数组 - 力扣（LeetCode） (leetcode-cn.com)，要求时间O(m+n)。改进：输入的两个数组各自有序，有可能分别是升序，降序情况

三面（约40min
项目整体设计思路与逻辑、架构（感觉很棒的是面试官从项目本身的需求出发，一起探讨了项目的设计和方向，还给项目提出了建设性意见，而不是模板式的让我说有什么难点、解决方案）
前端是怎么学的？
promise原理与实现（我答了发布订阅模式的实现方法，说逻辑没让写代码）
那已经有发布订阅模式了，为什么还要promise（我答promise是用这个模式来解决异步回调地狱问题balabala，扯到了事件循环）
事件队列保存在哪？执行栈呢？
HR面（约20min
时间不长，主要聊了爱好、为什么选择前端？学习方法？详细聊了聊之前的实习经历的工作？读不读研、职业规划？可以实习的时间，公司待遇方面的介绍。

### 字节跳动飞书部门前端开发岗实习一面面经
1.聊天（怎么学、什么时候开学、什么时候来、为什么学前端）

2.了解事件流吗

3.说说BFC

4.说说盒子模型

5.先看题：

typeof 1 === ''

typeof '1' === ''

typeof true === ''

typeof null === ''

typeof undefined === ''

typeof function() {} ===‘’

6.
console.log("start")

setTimeout(()=>{

console.log('timer1')

new Promise(function(resolve){

console.log(" promise start ")

resolve();

}).then(function() {

console.log('promise1')

})

}, 0)

setTimeout(()=>{

console.log('timer2')

Promise.resolve().then(function() {

console.log('promise2')

})

}, 0)

console.log("end")

7.讲讲事件循环

8.聊聊项目，怎么实现的蓝牙通信等

9.算法题：

给定一个升序整形数组[0,1,2,4,5,7,13,15,16]，

找出其中连续出现的数字区间，然后以下列方式进行重组：

["0->2", "4->5", "7", "13", "15->16"]

-----算法题写了个大概，勉强过了，接着聊Vue-----

10.讲讲computed、watch、filter的使用区别

11.computed数据改变后是立即渲染吗，确定是懒计算吗

12.watch主要是用在什么地方

13.prop和data有什么区别，prop会被observer双向绑定吗

14.如果修改props页面会展示修改后的结果吗，会有什么警告

15.用过Vuex吗，什么时候会使用vuex

16.vuex中的state是怎么被改变的，有多少种方式改变

17.讲讲这个组件间通信的方式

18.如果有一个非常复杂的组件，下面有很多组件，怎么确保observer渲染的顺序和watch只会加载一次？（说实话，题都没听懂）

19.了解过vue的异步更新吗，原理是什么

20.补充：捕获和冒泡是怎么设置的？addeventListener的第三个参数除了设置事件流还能写什么？

----
### 字节跳动飞书 前端 日常实习 一二面(已offer)

一面 (2.28 60min)
自我介绍
项目做了哪些事情？
项目过程遇到了哪些难点？
项目中用虚拟列表做了什么？
axios 项目有没有做出什么新的东西？
事件循环
虚拟DOM
React 代码如何变成真实 dom 的？JSX 怎么用 React.createElement 创建？
HTTPS
HTTP2.0/3.0
前端安全，CSRF 如何防护？
算法题：
假设一共有 n 个人，给出一个数组指出哪些人可以把东西传给哪些人？最大传递次数为k。计算传给第 n-1 个人一共有几种方式，传不到返回0
Example: n = 5, arr = [[0, 2], [0, 4], [2, 1], [1, 3], [4, 1], [2, 3], [3, 4]], k = 3
二面 (3.02 55min)
自我介绍
项目介绍，挑战、难点、解决方案
设计一个微前端框架需要注意哪些方面？隔离，子应用资源加载分别怎么做？
服务器端渲染，解决了哪些问题
自动化测试有了解吗？
React diff算法，为什么需要hooks？
有了解过哪些新技术？跳坑了，我瞎说webpack5和pnpm结果都啥也不知道.......
webassembly和node这些有了解过吗？有没有实际开发经验？
做题：一道闭包，一道promise，一道二叉树求路径和

### 字节 国际化电商前端一面22

打印螺旋矩阵
react hooks有哪些
useCallback和useMemo的区别
useState作用是什么
key的作用
考察闭包输出
0.1 + 0.2 === 0.3？
十进制怎么转化为二进制呢？
'1' + 2 = ?
1+'2' = ?
大数相加
http1.1和2.0的区别
拥塞避免是怎么做的



### 字节跳动 飞书前端 暑期实习 一二三面（OC）
1. 自我介绍
2. 项目介绍
3. React Hooks 与 React Component 的关系区别
4. 如何用 Hooks 模拟 componentDidMount 与 componentWillUnmount
```
useEffect(() => {
    // componentDidMount
 
    return () => {
        // componentWillUnmount
    }
}, [])
 
useEffect(() => {
    // componentDidMount + componentDidUpdate
})
 
React.memo(fnComp, (prevProps, nextProps) => {
    // shouldComponentUpdate
})
```

1. 如何优化对 React 组件进行优化？
2. useMemo 和 useCallback 的区别？useCallback 的应用场景。
3. React Hooks 的实现细节？（不会）
4. React 父子件通信及应用场景。
5. MobX 解决了什么问题？项目中如何实际使用 MobX？
MobX 在异步的情况下如何进行值的更新？
了解 MobX 6 吗？其 makeAutoObserver(this) 的 shadow, ... 的细节聊聊（不会）
MobX 如何解决响应式更新？如何解决变量挟持？
10. TypeScript 的泛型及应用，Interface 与 Type 的区别，TypeScript 的高阶用法（Pick,...)，详细聊聊 Omit。
https://juejin.cn/post/6844904184894980104


1.  垂直居中的实现方案
2.  flexbox 的一些坑
3.  介绍一下盒子模型
4.  z-index 在什么情况下会失效
5.  position: sticky 的作用
6.  如何实现 1px 在手机上？使用 transform: scale() + width/height * 2
7.  如何看待 CSS 预处理器？
8.  如何解决跨域问题？为什么会产生跨域问题？
9.  编程题：使用 Promise 实现 sleep，且加上 TypeScript 类型
1
2
3
4
5
async function sleep(timeout): Promise<void> {
  return new Promise((resolve) => {
    setTimeout(() => resolve(), timeout)
  })
}


21. 算法：二叉树的路劲总和（写了好久，因为没有想清楚）
22. 算法： 最长严格递增序列（如何优化？）：写的 dp（这边也写了很久），问如何优化：贪心+二分（没写）。

我差点以为我要挂了。

二面

1. 自我介绍&项目介绍
2. 前端最吸引你的一点？为什么开始学习前端？
3. 前端的学习对你有其他带来负担吗？
4. 尝试实现过 React / Vue 吗？
聊聊 React Fiber/React 优先级 lane 与更新/Hooks/分片渲染？
5. 你最有挑战的项目？为什么？规模体现在哪？
6. WebSocket 在什么情况场景下运用的？你在项目中主要负责什么？如何解决乱序问题（时间戳+Immutable.js）
7. TypeORM 的引入是为了解决什么问题？聊聊 SQL 注入。如何工作？如何避免（Prepared SQL+转义）。
8. 还有什么安全问题？XSS。实现原理？如何避免
9. Webpack 与 Vite 的区别？介绍一下 Vite。Vite 的优势在哪？
10. 有办法实现一个 AST 解析器吗？聊一下 AST。
11. 了解正则的原理吗？（不了解）。
基于 DFA/NFA 的匹配。
https://segmentfault.com/a/1190000021787021

12. 手写题：写一个邮箱匹配的正则
1
 /^[A-Za-z0-9]+([_\.][A-Za-z0-9]+)*@([A-Za-z0-9\-]+\.)+[A-Za-z]{2,6}$/
https://juejin.cn/post/6844903795386744845

13. 手写题：非常简单的一个词法分析器（只分析赋值），其实挺简单的，主要是我在想怎么让他更通用一点就瞎写了好久。
（还好面试官没有卡我这两个手写题：意思到了就行）

三面
1. 自我介绍/项目介绍
2. 项目介绍，负责部分（全栈）并大概介绍项目架构，挑战（并发：消息队列、Websocket Relay；等）
3. 学校项目的挑战（分别列举）
4. React setState 原理
5. 手写题：返回给定七个扑克牌是否有同花顺，数据结构 `[{num: 1, hua: 's'}, ...]`
输入
hua: HXMF
 
const cards = [
  {num: 1, hua: 'H'},
  {num: 2, hua: 'H'},
  {num: 3, hua: 'H'},
  {num: 4, hua: 'H'},
  {num: 5, hua: 'H'},
  {num: 2, hua: 'X'},
  {num: 2, hua: 'M'},
]
const CARD_HUA_MAP = {
  'H': 0,
  'X': 13,
  'M': 26,
  'F': 39,
}
function isSameHuaShun(cards: { num: number, hua: string }[]) {
  const sorted_nums = cards.map((i) => i.num + CARD_HUA_MAP[i.hua]).sort()
  let count = 1;
  for (let i = 1; i < sorted_nums.length; i++) {
    if (sorted_nums[i - 1] === sorted_nums[i] - 1) {
      count++;
    } else {
      count = 1;
    }
 
    if (count === 5) {
      return true;
    }
  }
 
  return false;
}



1. 实现一个 EventEmitter: on, emit, off, once

type FnCallback = (...args) => any
 
class EventEmitter {
  eventMap: { [key in string]?: FnCallback[] } = {}
 
  constructor() {}
 
  on(event: string, fn: FnCallback) {
    const listeners = this.eventMap[event] || (this.eventMap[event] = [])
    listeners.push(fn)
  }
 
  emit(event: string, ...args: any) {
    this.eventMap[event]?.forEach((fn) => {
      fn.call(null, args)
    })
  }
 
  off(event: string, fn: FnCallback): void {
    if (!this.eventMap[event]) return
    this.eventMap[event] = this.eventMap[event].filter((cn) => fn !== cb)
  }
 
  once(event, fn: FnCallback) {
    this.on(event, (...args: any) => {
      fn.call(null, args)
      this.off(event, fn)
    })
  }
}

### 字节跳动-今日头条-前端暑期实习一二三面 


一面 2022/2/28：48min
自我介绍

项目的轮播图怎么实现的

transition 如何检测动画结束。不懂

讲一下 box-sizing 的值和对应的作用

如何实现水平垂直居中

讲一下防抖和节流和应用

写一个防抖

第一次写没有把 timeout 赋值，面试官文 clearTimeout(undefined) 会怎么样，不清楚说了可能会报错，然后把 null 补上了

讲一下图片懒加载是怎么实现的

图片在加载的时候出现了抖动应该怎么解决

图片太多的话，可能会造成页面卡顿，如何解决这个问题

按你刚说的，每次都得进行图片的重新请求加载，有没有什么办法可以不请求

你项目上用了 websocket，讲一下

如果服务器是分布式的话，怎么保持客户端和服务器只有一个连接

讲一下 jwt 保存了什么 。

如果 jwt 被劫持了，别人用这个 jwt 发出请求，服务器如何鉴别出这个 jwt 是不合法的

除了 jwt 还有什么方式进行登录鉴权

用户名和密码怎么存储在数据库（绕了一圈才知道什么意思。。）

密码加密存在数据库的话，使用对称加密好还是非对称好

那 MD5 能不能解密

那如果你的数据库被盗取的话，加密了的密码安全嘛

讲一下跨域和解决方法

CORS 要是想发 cookie 的话怎么设置。

Promise代码：

第二个答错了，一直在想 then 函数功能还是说错了。。。应该是 undefined

 new Promise((resolve, reject) => {
     resolve(123);
 }).then(data => {
     console.log(data);
 }).then(data => {   
     console.log(data);
 })
作用域考核

11 11 6

后面问把 var m 改成 let m 结果怎样：NaN NaN 6

var m = 10;
function fn() {
    return this.m + 1;
}
var obj = {
    m: 5,
    test1: function() {
        return fn();
    }
};
obj.test2 = fn;
 
console.log(obj.test1(), fn(), obj.test2())
url 参数提取

忘了写 decodeURICompoment，提示了补上了

问：decodeURICompoment 和 decodeURI 有什么区别 ，应用场景

对称二叉树

反问

二面 2022/3/4：60min
自我介绍

项目有没有什么亮点

项目的轮播图怎么实现的

前后添加两张图片

能不能只添加一张

分析如果添加一张的情况，好像没办法。面试官说那我现在就告诉你一张也行，怎么弄呢？

思考了一会，突然茅塞顿开，和面试官讲了思路。面试官说现在很多人都用组件了，自己写轮播图也是个亮点

讲一下你知道的前端优化

前端怎样缓存

那强缓存如果时间没到期，可是文件修改了。

有没有看过webpack打包后的js、css文件

试官讲了其实在文件名上加上通过对文件内容进行hash运算，生成一个文件的唯一hash字符串(如果文件修改则hash号会发生变化)，替换文件名，生成一个带版本号的文件名 ，从而达到更改引用URL的目的

讲一下async和defer

在vue中的话使用async和defer会有什么缺点

讲一下事件循环

宏任务和微任务的优先级。宏任务优先

宏任务和微任务分别有哪些

一个事件循环输出题 √

讲一下MVVM的优缺点

讲一下虚拟DOM如何更新

讲了DIff算法

DIff算法是广度的还是深度的

讲一下vue的key值

vue组件间的通信

vue的slot

讲了一下作用和作用域插槽

写个请求，能判断超时 √

10w条数据，1条请求能获取1000条数据，现在能同时发3个请求，写一个函数实现。其实就是写一个带并发限制的异步调制器，每次能并发三条请求

面试官：那如果请求超时怎么办？使用上一题写的函数进行判断，超时则重新发送自己的请求

面试官：其实不用写太多判断的，超时的时候把请求push回数组就行。茅塞顿开，问面试官还需不需要写，面试官说不用了，思路明白了就行

反问
三面 2022/3/8：40min
关于项目的偏多，面试体验很好，偏聊天

自我介绍

介绍项目和困难点

项目实在水没啥好说的

项目如何重构的

项目的哪些模块是你做的

为什么用vue

有没有了解其它框架比如react

讲一讲react的思想

只说了函数式编程和composition api，实在不懂

说了vue和react都是基于MVVM框架开发的

讲一下MVVM框架

讲了MVC和MVVM

MVVM的好处

原生js很多功能都能实现，为什么要有这些框架

有没有看过vue或react的源码

看过vue2的

讲一讲看了哪些

双向绑定

diff算法

讲一讲diff算法

讲了虚拟dom和diff算法的过程

项目之后的目标

项目的拍板人是？导师

那如果有些功能导师觉得没必要之类的，你要怎么去说服导师去认可你们的想法

讲一讲你的微信小程序，是用来学习的嘛？

是，用来学习如何做小程序，讲了为什么不使用原生的而是用 uni-app 写

讲一讲微信小程序和H5的渲染区别（答得不太好，对小程序不是很了解）

说了微信小程序有个双线程的概念

H5的渲染过程

项目用到jwt，讲一讲jwt

讲了使用jwt鉴权的过程

jwt的组成部分
后端返回给前端的jwt是一串字符串，文本通过 "." 链接一起就构成了Jwt字符
讲一讲 token和jwt的区别。

主要讲了token需要在后端保存数据，jwt不需要，保存在客户端

都可以用来鉴权，记录用户信息

有没有了解数据库

比较少

实习最想学到什么

最后说了最想转正（面试官笑了hhh）

你觉得平时开发js 和写nodejs有什么区别

实在不会，说思想应该差不多，但是引擎不一样

说了 node 会有中间件和express和koa等框架

你想做前端还是nodejs

都想，讲了之后如果能的话想前端和nodejs都做

有没有考虑后端，java这种

说目前想先把前端这个方向做好

想在工作一年后到达什么水平

把前端技术做扎实

有没有自己偏向产品，常用哪些app

微博、虎扑、知乎等。面试官说那你可能比较适合做头条

反问
HR面 2022/3/11：30min


### 2022春招字节前端面经
作者：Pegessi
链接：https://www.nowcoder.com/discuss/857251?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647165561618
来源：牛客网

八股文
输入url到显示网页的过程
着重问了dns解析
OSI七层网络模型
csrf与xss攻击
你知道的其他攻击方式
洪泛攻击与sql注入
promise async&await setTimeout运行顺序
promise状态转变机制
原型链说一下
复杂请求post时的预检机制
new完成了什么工作，自己写一下new函数
匿名函数与词法作用域-原型链实战
算法题
找数组最小的k个数（最好用桶排）
不连续子数组和（乱序数组，找不连续位序的最大子数组和）

### 春招 字节前端一面面经


1、自我介绍
2、什么时候开始学前端的？为什么要学前端？
3、说一下盒模型
4、知道浏览器的跨域吗？怎么解决。
只说了jsonp,   其他方法不记得了
5、cookie，localstorage, sessionStorage的区别
这个我没背好，这么基础的问题，我哭。
6、简单说一下promise。
说了下三种状态
7、promise.all()的作用，什么时候会用？
8、写一个css布局，三个div分为左，中，右三栏
我用的flex，又问了下子元素flex的各种属性，有什么值，什么作用
9、（接上题）还有没有别的方法
想不起来了，没答上
10、 用两个栈模拟队列的出队和入队
写是写出来了，但面试官大大说我写的和他想的不一样（我怎么知道你想的是什么呢！哭哭）
11、实现深拷贝
没写出来，太尴尬了
12、let，var, const的区别，问了道关于变量提升的题
13、问了项目相关的问题（怎么分工的？有没有用到cookie?是自己写的接口还是用的自带的？）
14、反问
我问了我现在最欠缺什么？是项目经验还是基础知识还是什么
答：项目经验少了点，学前端的时间也短了点，但看出我还是有所准备的。

over.


### 字节跳动前端面经（1面+2面）2023

1面（50min）：
1. CSS实现中间自适应，两边固定300px(手写代码
2. 输出题(需要阐述原因)：

var a = function () { this.b = 3 };
var c = new a();
a.prototype.b = 9;
var b = 7;
a();
// 给出下面的执行结果
console.log(b);
console.log(c.b);
这样呢？

var a = function () { this.name = 3; }
var c = new a();
a.prototype.b = 9;
console.log(c.b)
1. 输出题(需要阐述原因)：

setTimeout(function() {
    console.log("setTimeout");
})
new Promise(function(resolve) {
    console.log("promise");
    for (var i = 0; i < 10000; i++) {
      if(i === 10) {
          console.log("for");
      }
      if(i === 9999) {
          resolve("resolve");
      }
    }
}).then(function(val){
    console.log(val)
});
console.log("console");
1. 说说HTTP和HTTPS -> 追问数字证书的作用
2. 说说跨域的解决方案 -> 追问了解 CORS的预检请求吗
3. 描述VueRouter如何实现单页
4. 写代码

function parseUrl(url) {
    // 代码实现这个函数
}
console.log(parseUrl("https://a.b.come?aaa=123&bbb=hhah&ccc=456"));
// 希望返回如下
{
    aaa: "123",
    bbb: "hhah",
    ccc: "456"
}
console.log(parseUrl("https://a.b.come?aaa=123&bbb=hhah&ccc=456&ccc=789"))
// 希望返回如下
{
    aaa: "123",
    bbb: "hhah",
    ccc: ["456", "789"]   
}
1. 求二叉树的公共父节点
2面（60min）：
1. 外边距塌陷产生的原因 -> 如何解决
2. 如何给图片设置一个兜底图
3. utf-8 编码 -> 常见的汉字字符占几个字节
4. 你了解有哪些 HTTP 头字段 -> 说的越多越好
5. 如何判断 ip 地址是哪类( A类，B类，C类这种
6. HTTP缓存谈谈(越多越好
7. 缓存我谈到了CDN -> CDN的作用 ,CDN为什么快
8. CDN和DNS之间的关系
9. 0.1 + 0.2 不等于 0.3 的原因 -> 还追问了我小数如何转二进制
10. import 和 require 的区别 -> 为什么有这两种模块化
11. JS中如何创建一个可读的对象 -> 本来我答的是 Object.defineProperty，后来答到了Object.freeze()
1
2
3
4
5
6
7
var object = {"a" : [{"b": {"c" : 3}}]};
get(object, "a[0].b.c");
// => 3
get(object, ["a", "0", "b", "c"]);
// => 3
get(object, "a.b.c", "default");
// => "default"
12. 没时间了，求两个整数数组中的公共数字（交集）


### 字节跳动 抖音前端 实习面经（三面+HR面，已入职

作者：西行寺悟空
链接：https://www.nowcoder.com/discuss/861304?type=post&order=create&pos=&page=1&ncTraceId=&channel=-1&source_id=search_post_nctrack&gio_id=27015C6C0BF46F9236ECD1AAD0BB463D-1647147820632
来源：牛客网

面试问题
一面（约40min
介绍项目

jwt在项目中的具体实现，必要性？为什么不用微信API的鉴权？（答官方文档建议开发者自定登录态）

tcp与udp区别？应用场景？

get与post区别，应用场景？在项目中的使用？

http缓存控制，协商缓存？

https如何保证安全的？加密方式？公私钥交换过程？

跨域是什么？产生条件？在微信小程序中的运用？解决了什么？

jsonp有了解过吗？（答没有什么了解，之前看到跨域解决方案的时候有看到过对比，没有深入了解，熟悉的是cors和nginx反向代理。然后也没有追问下去了）

看输出，解释原因

// 1.局部作用域与全局作用域
let val = 1;
function foo() {
  console.log(val);
}
function bar() {
  let val = 2;
  foo();
}
bar();
 
// 2.this指向
window.name = 'ByteDance';
function A() {
  this.name = 123;
}
A.prototype.getA = function () {
  return this.name + 1;
};
let a = new A();
let funcA = a.getA;
console.log(funcA());
// 解释完上面答下面这种情况
console.log(a.getA());
 
// 3.this指向(call)
const obj = {
  birth: 1990,
  getAge(year) {
    let fn = y => y - this.birth;
    return fn.call({ birth: 2000 }, year);
  },
};
console.log(obj.getAge(2020));
 
// 4.执行顺序
async function async1() {
  console.log('async1 start');
  await async2();
  console.log('async1 end');
}
async function async2() {
  console.log('async2');
}
console.log('script start');
setTimeout(() => {
  console.log('setTimeout');
}, 0);
async1();
new Promise(function (resolve) {
  console.log('promise1');
  resolve();
}).then(function () {
  console.log('promise2');
});
console.log('script end');
算法：栈模拟队列 剑指 Offer 09. 用两个栈实现队列 - 力扣（LeetCode） (leetcode-cn.com)
二面（约70min
介绍项目，看项目后端中某个具体功能的具体代码（图片上传与处理）

实习经历？（简历上写的hr岗怎么就整开发了呢？噢，原来是用python编写脚本、使用文档，提升部门某项重复性耗时工作的工作效率）

浏览器不同标签页面通信？同源、跨域情况下？（可能我一直都没答到点子上，一直让我说有没有其他的方案，说了好几个能想到的，包括storage api,server侧配合websocket甚至外部应用程序

localStorage，sessionStorage区别？

css实现三角形！（我答的transform: rotate(45deg)然后在父元素overflow: hidden，插问了rotate的旋转中心怎么确定。总之是没答到正解border的点子上）

css position属性有哪些？区别是什么？详细说说fixed的定位方式？

看输出，解释原因


//1也是关于this的，还有闭包，和一面差不多
 
//2. 作用域？变量提升？
for(var i=0;i<5;i++){
  setTimeout(()=>{
    console.log(i);
  },0)
}
//3也是关于event loop的，和一面的执行顺序差不多，让具体解释了一下宏任务和微任务
算法：查找json中的children路径
现有如下json（简化为对象），已知每个节点id唯一，编写findNode(id)，返回路径，如findNode(5) 输出 1->4->5
（直接DFS就行，当时一下没想好回溯写了半天没写对，面试结束后两分钟搞定了）


{
  id: 1,
  children: [
    { id: 2, children: [{ id: 3, children: [] }] },
    {
      id: 4,
      children: [
        { id: 5, children: [] },
        { id: 6, children: [] },
      ],
    },
    { id: 7, children: [] },
  ],
};
算法：合并两个有序数组88. 合并两个有序数组 ，要求时间O(m+n)。改进：输入的两个数组各自有序，有可能分别是升序，降序情况

三面（约40min
项目整体设计思路与逻辑、架构（感觉很棒的是面试官从项目本身的需求出发，一起探讨了项目的设计和方向，还给项目提出了建设性意见，而不是模板式的让我说有什么难点、解决方案）
前端是怎么学的？
promise原理与实现（我答了发布订阅模式的实现方法，说逻辑没让写代码）
那已经有发布订阅模式了，为什么还要promise（我答promise是用这个模式来解决异步回调地狱问题balabala，扯到了事件循环）
事件队列保存在哪？执行栈呢？
HR面（约20min
时间不长，主要聊了爱好、为什么选择前端？学习方法？详细聊了聊之前的实习经历的工作？读不读研、职业规划？可以实习的时间，公司待遇方面的介绍。