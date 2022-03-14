>连八股文都不懂，怎么敢在前端混下去？

### let const var
let声明变量，const声明常量，let声明的变量在未声明前会出现不允许使用，会出现「暂时性死区」
var没有块的概念，可以先使用，后声明，因为有“变量提升”
let，const只能在块内访问，必须初始化。

- 暂时性死区是浏览器的一个bug，当访问一个未声明的变量不会报错而是``undefind``。在程序中从进入作用域到可被访问的一段时间称为「暂时性死区」
- 变量提升只针对var，在js执行时会先解析代码，获取所有被声明的变量，然后将「变量声明语句」提升到代码的头部，这就叫做变量提升

const指向的地址不可以变化，但是指向地址的内容可以变化，对象和数组是引用类型，保存的只是引用对象的指针。

### es6新语法
- set：类似于数组但是成员值唯一
- map：键值对数据结构
  - map和object的区别：
    1. object的key只能为string或者symble，map为任意值
    2. map为有序键值对
    3. map键值可以从size() 获取
    
### 箭头函数和普通函数
- 没有自己的this，super，arguments和new.target绑定
- 不能使用new来调用
- 没有原型链
- 不能改变this的绑定
- 没有this的绑定，必须通过查找作用域链来决定其值
  - 如果被非箭头函数包含，则指向的是最近一层非箭头函数
  - 否则为全局对象

### JS 中 this 的五种情况

1. 作为普通函数执行时，this指向window。
2. 当函数作为对象的方法被调用时，this就会指向该对象。
3. 构造器调用，this指向返回的这个对象。
4. 箭头函数 箭头函数的this绑定看的是this所在函数定义在哪个对象下，就绑定哪个对象。如果有嵌套的情况，则this绑定到最近的一层对象上。
5. 基于Function.prototype上的 apply 、 call 和 bind 调用模式，这三个方法都可以显示的指定调用函数的 this 指向。apply接收参数的是数组，call接受参数列表，`` bind方法通过传入一个对象，返回一个 this 绑定了传入对象的新函数。这个函数的 this指向除了使用new `时会被改变，其他情况下都不会改变。若为空默认是指向全局对象window。


### 原型 && 原型链
原型关系：

- 每个 class都有显示原型 prototype
- 每个实例都有隐式原型 _ proto_
- 实例的_ proto_指向对应 class 的 prototype

‌ 原型:  在 JS 中，每当定义一个对象（函数也是对象）时，对象中都会包含一些预定义的属性。其中每个函数对象都有一个prototype 属性，这个属性指向函数的原型对象。

原型链：绝大部分函数都有一个prototype属性，含义是函数的原型对象，所有被创建的对象都可以访问原型对象的属性和方法。在new的过程中，会将函数的prototype赋值给对象的__proto__属性，当访问一个对象的属性的时候，如果对象内部不存在这个属性，就从__proto__所指的父对象寻找，一直找到终点null，通过__proto__属性连接的这条链就是原型链。

> 原型链最顶端：``Object.prototype.__proto__=null``
### new一个对象的过程
1. 创建一这个函数为原型的控对象
2. 将函数的prototype属性传递给_proto_
3. 将对象作为this传进去，有return就返回return内容，没有return就创建一个新对象


### 基本类型和引用类型
基本类型：

String、Boolean、Number、Null、Undefined、Symbol,还有一个还没有被正式纳入标准的BigInt。

Symbol可以用来创建唯一常量。

基本类型的值不能被方法来改变，只能通过赋值的方式来改变，所谓“赋值”就是“指针指向的改变”，
基本数据类型的值不能添加方法和属性
一个变量向另一个变量赋值，是会在变量对象上创建新值，把新值复制到新变量分配到位置上，两个变量独立且不互相影响
基本数据类型的比较是值的比较
基本数据类型是存放在栈区的，变量的标识符和变量的值


引用类型：

引用类型统称为Object 类型，细分的话包括Object 类型、Array 类型、Date 类型、RegExp 类型、Function 类型

引用类型的值是可以改变的
引用类型可以添加属性和方法
引用类型的值是按照引用访问的，当从一个变量向另一个变量赋值引用类型的值时，同样也会将储存在变量中的对象的值复制一份放到为新变量分配的空间中.引用类型保存在变量中的是对象在堆内存中的地址，所以，与基本数据类型的简单赋值不同，这个值的副本实际上是一个指针，而这个指针指向存储在堆内存的一个对象.那么赋值操作后，两个变量都保存了同一个对象地址，而这两个地址指向了同一个对象.因此，改变其中任何一个变量，都会互相影响
引用类型的比较是引用的比较
引用类型的值是同时保存在栈区和堆区中的

### 事件循环、宏任务和微任务
浏览器端事件循环中的异步队列有两种：macro（宏任务）队列和 micro（微任务）队列。

- 常见的 macro-task 比如：setTimeout、setInterval、script（整体代码）、 I/O 操作、UI 渲染等。
- 常见的 micro-task 比如: new Promise().then(回调)、MutationObserver(html5新特性，提供了监视对DOM树所做更改的能力) 等。
当某个宏任务执行完后,会查看是否有微任务队列。如果有，先执行微任务队列中的所有任务，如果没有，会读取宏任务队列中排在最前的任务，执行宏任务的过程中，遇到微任务，依次加入微任务队列。执行栈空后，再次读取微任务队列里的任务，依次类推。


### apply,call,bind区别
三者都是用于改变函数体内this的指向，但是bind与apply和call的最大的区别是：bind不会立即调用，而是返回一个新函数，称为绑定函数，其内的this指向为创建它时传入bind的第一个参数，而传入bind的第二个及以后的参数作为原函数的参数来调用原函数。

apply和call都是为了改变某个函数运行时的上下文而存在的（就是为了改变函数内部this的指向）；apply和call的调用返回函数执行结果；

如果使用apply或call方法，那么this指向他们的第一个参数，apply的第二个参数是一个参数数组，call的第二个及其以后的参数都是数组里面的元素，就是说要全部列举出来；

### promise
为什么要有promise
- promise.all
- promise.race

### 跨域
> 浏览器的一种保护措施：同源策略：「协议+域名+端口相同」

1. jsonp跨域：
jsonp原理：静态文件不受同源政策影响，我可以返回一个script里面有一个回调函数，函数的里面是我要的东西
```
<script>
    var script = document.createElement('script');
    script.type = 'text/javascript';

    // 传参一个回调函数名给后端，方便后端返回时执行这个在前端定义的回调函数
    script.src = 'http://www.domain2.com:8080/login?user=admin&callback=handleCallback';

    document.head.appendChild(script);

    // 回调执行函数
    function handleCallback(res) {
        alert(JSON.stringify(res));
    }
 </script>
 ```

2. document.domain + iframe跨域
此方案仅限主域相同，子域不同的跨域应用场景。

实现原理：两个页面都通过js强制设置document.domain为基础主域，就实现了同域。
```
父窗口：http://www.domain.com/a.html

<iframe id="iframe" src="http://child.domain.com/b.html"></iframe>
<script>
    document.domain = 'domain.com';
    var user = 'admin';
</script>


子窗口：(http://child.domain.com/b.html)
<script>
    document.domain = 'domain.com';
    // 获取父窗口中变量
    alert('get js data from parent ---> ' + window.parent.user);
</script>
```

3. 跨域资源共享（CORS）


为什么选择CORS？ 因为jsonp只支持get请求，但我们还有post请求，CORS就满足了我的要求。服务端设置响应头中的Access-Control-Allow-Origin为对应的域名。

（必须）Access-Control-Allow-Origin: *
（可选）Access-Control-Allow-Credentials: true//表示允许是否发送cookie，默认情况下cookie不包含cros请求中
（可选）Access-Control-Expose-Headers: name//携带上制定响应头的字段
如果CORS请求了非简单请求，还会带来进行option请求预检的问题
- 非简单请求：
  请求方法是以下三种方法之一：
HEAD
GET
POST
HTTP的头信息不超出以下几种字段：
Accept//客户端或代理能够处理的媒体类型
Accept-Language//优先的语言（中文、英文……）
Content-Language// 实体主体的自然语言
Content-Type：只限于三个值application/x-www-form-urlencoded、multipart/form-data、text/plain
凡是不同时满足上面两个条件，就属于非简单请求。

服务器收到"预检"请求以后，检查了Origin、Access-Control-Request-Method和Access-Control-Request-Headers字段以后，确认允许跨源请求，就可以做出回应。如果服务器否定了"预检"请求，会返回一个正常的HTTP回应，但是没有任何CORS相关的头信息字段。这时，浏览器就会认定，服务器不同意预检请求，因此触发一个错误，被XMLHttpRequest对象的onerror回调函数捕获。

4. nginx反向代理接口跨域

5. WebSocket协议跨域
WebSocket protocol是HTML5一种新的协议。它实现了浏览器与服务器全双工通信，同时允许跨域通讯，是server push技术的一种很好的实现。

原生WebSocket API使用起来不太方便，我们使用Socket.io，它很好地封装了webSocket接口，提供了更简单、灵活的接口，也对不支持webSocket的浏览器提供了向下兼容。


### 闭包
> 闭包："有权访问另一个函数作用域中变量的函数"



```
function fun(){
  var num = 1;
  return function () {
    console.log(++num)
  }
}

var count = fun()
count()//2
count()//3
count()//4
```
闭包的优点：延长局部变量的生命周期

闭包缺点：会导致函数的变量一直保存在内存中，过多的闭包可能会导致内存泄漏

### 垃圾回收
- 标记清除（常用）：当变量进入执行环境时，被标记为“进入环境”，当变量离开执行环境时，会被标记为“离开环境”。垃圾回收器会销毁那些带标记的值并回收它们所占用的内存空间。
- 引用计数：跟踪一个值的引用次数。缺点：可能会引起内存泄漏（对象A包含指向对象B的指针，对象A包含对象A的引用）

### 浏览器渲染帧
>浏览器一帧数据的渲染：60hz==16ms刷新一次数据

相关的两个进程
- GPU进程：负责绘制
  - GPU主线程 
- 渲染进程：
  - 排版线程：负责启动主线程
  - 栅格化线程：CPU ---> GPU
  - 主线程

1. 由排版线程决定是否启动主线程，主线程决定渲染逻辑，最终交给GPU绘制到页面
（光标闪烁不会启动主线程）
2. 渲染进程又分为一下几种操作
   1. 处理输入
   2. requestAnimationFrame：执行动画
   3. 解析js，css生成DOM树（可能会阻塞页面的渲染）
   4. 计算生成CSSTree
   5. 合并生成Layout Tree，交给排版线程
   6. GPU绘制，发送到页面

### 进程，线程的区别
【区别】：
调度：线程作为调度和分配的基本单位，进程作为拥有资源的基本单位；
并发性：不仅进程之间可以并发执行，同一个进程的多个线程之间也可并发执行；
系统开销：进程创建或者销毁开销大，一个进程崩溃不会影响其他。线程之间没有独立的地址空间。
【联系】：
一个线程只能属于一个进程，而一个进程可以有多个线程，但至少有一个线程；
资源分配给进程，同一进程的所有线程共享该进程的所有资源；
处理机分给线程，即真正在处理机上运行的是线程；
线程在执行过程中，需要协作同步。不同进程的线程间要利用消息通信的办法实现同步。

### ES6模块和CommonJs模块
ES6:对模块的引用，import导入为只读状态，不可修改，只能顶层使用，编译时加载
CommonJs：对模块的浅拷贝，可以改变require引入的变量，任何地方都可使用，运行时加载
（为服务端开发设计的，同步导入读取文件内容）


### 深拷贝，浅拷贝
- 浅拷贝：只复制某个对象的指针，不复制对象本身，共享一块内存
- 深拷贝：复制并且创建一个一摸一样的对象，不共享内存，新旧对象互相不影响

### JS判断数据类型
1. typeof [] === 'object'
2. typeof null === 'object'
3. Array.isArray() //判断数组
4. Object.prototype.toString.call(1) //'[object Number]'

### 事件委托

> 利用事件冒泡，只处理某一个事件的处理程序，从而管理某一类型的所有事件

好处:只绑定一次事件，无需频繁访问DOM，性能较高。
当有新的DOM生成时，无需重复绑定事件，代码清晰简洁。

### React合成事件
React基于虚拟DOM实现了一个事件合成层，我们定义的事件处理器会接收到一个合成事件的实例。
实现机制：
React并不会把事件处理函数直接绑定到真实dom上，而是通过``ReactEventListener``把所有事件绑定到最外层节点，依赖冒泡来实现事件委派

### 冒泡，捕获
微软提出了冒泡的事件流，从最内层开始向上传播直到Dom对象
网景提出了捕获的事件流，从最外层到具体元素
w3c制定了统一的标准：**先捕获再冒泡**

可以通过``addEventListener()``第三个参数来确定是捕获还是冒泡，默认为false，代表冒泡。
useCapture：布尔值，规定是否是捕获型，默认为 false（冒泡）。因为是可选的，往往也会省略它。

addeventListener的第三个参数除了设置事件流还能写什么？
- 对象``{}``
```
el.addEventListener(type, listener, {
    capture: false, // === useCapture 
    once: false,    // 是否设置单次监听
    passive: false  // 是否让 阻止默认行为(preventDefault()) 失效
```



---

- __HTTP__
- __CSS__
- __React/Vue__
- __webpack__
- __浏览器__
- __性能优化__
- __node__
- ......

不知道从什么时候开始，这些东西就开始叫八股文了🧐，前端也不再是HTML+CSS+jQuery的时代了。
学的也越来越多，接触到的思想也越来越多。打包工具五花八门，前端也越来越工程化。头发也掉的越来越多👨‍🦲