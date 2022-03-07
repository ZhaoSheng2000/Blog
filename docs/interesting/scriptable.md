## 灵感来源

受益于最近抖音上面一些推广app的视频，其中有一个是可以将自己的照片，文字等发送到情侣的桌面小组件上，主打「情侣」、「恋爱」这类标签。并且还挺多人喜欢这种......

试问：哪个男孩子会拒绝拥有一个专属ios小组件，甚至女朋友的照片呢？

身为一名合格的程序员就要有举一反三的能力，本着“能自己写就不麻烦别人”的原则，脑海中浮现了无数个骚操作🌠

- ReactNative ？「pass❌」
  
- Flutter ？「pass❌」
  
- Scriptable ！「yep✅」
  

### 说干就干

#### Scriptable的简单介绍

**工欲善其事，必先利其器**，我们先来了解一下[Scriptable](https://link.juejin.cn?target=https%3A%2F%2Fscriptable.app%2F "https://scriptable.app/")有哪些作用吧。从上面官网上的介绍我们可以知道，这个APP可以让我们**使用JavaScript来自动化iOS**。这句话是什么意思呢？就是我们可以提前编写好一些代码去执行一些特定的任务，比如：获取**GitHub**上面的**Trending**项目的名字和介绍、了解**Hacker News**的最新资讯、获取自己的最近日程、以及自己的TODO列表等等。包括上面所说的推广视频的效果一下子就浮现在眼前！

此外，**Scriptable**也支持许多特性，这些特性包括：

- **支持ES6语法**
- **可以使用JavaScript调用一些原生的API**
- **Siri 快捷方式**
- **完善的文档支持**
- **共享表格扩展**
- **文件系统继承**
- **编辑器的自定义**
- **代码样例**
- **以及通过x-callback-url和其它APP交互**

简直是前端的福音呀！

### 开始前的准备工作

- 一台升级到 **iOS 14** 的 **iPhone** 手机
- 安装 **Scriptable** 应用程序

在软件中会有一些官方示例供我们参考，还有一些api等等，这些内容看一下就好了。

打开示例后直接可以在手机上进行操作，编写代码。当然不是特别方便。那就来个传统的「Hello World」瞧瞧吧

```js
// Variables used by Scriptable.
// These must be at the very top of the file. Do not edit.
// icon-color: cyan; icon-glyph: greater-than-equal;


// 判断是否是运行在桌面的组件中
if (config.runsInWidget) {
  // 创建小部件
  const widget = new ListWidget();
  // 添加文本
  const text = widget.addText("Hello, World!");
  text.textColor = new Color("#000000");
  text.font = Font.boldSystemFont(36);
  text.centerAlignText();
  // 添加渐变色背景
  const gradient = new LinearGradient();
  gradient.locations = [0, 1];
  gradient.colors = [new Color("#F5DB1A"), new Color("#F3B626")];
  widget.backgroundGradient = gradient;
  // 设置部件
  Script.setWidget(widget);
}
```

看到显示出来的效果也还可以，但是毕竟在手机上不是特别方便。于是经过我的一番搜寻，找到了相关的[小件件开发框架](https://link.juejin.cn/?target=https%3A%2F%2Fgithub.com%2Fim3x%2FScriptables "https://github.com/im3x/Scriptables")：

它会将 PC 与 Scriptable 相连，然后我们就可以直接在 VSCode 上进行代码的编写，保存后会自动同步到手机上并自动运行。  
具体的操作方法在作者的文档上写的很清楚了，这里不多赘述。

接下来就是编码和实现步骤了

### 后记

#### 对小组件的一些思考

在实际操作过程中，发现现在许多的app都支持添加桌面小组件，可以让用户快速的触达一些想要浏览的关键信息，也可以直达具体的某些服务，对于我们来讲还是有很大的帮助的。

即使我没有相关的原生ios开发的经验，也可以借助这样的平台去实现一些有趣的，有价值，有意义的小组件。这无疑存在一些新的机遇。就像上面提到的共享小组件内容的类似app。

### 后后记 
目前已经完成了一个支持热更新的桌面小组件，使用上传的照片作为背景，还可以添加每日事项，以列表的形式展示出来，使用Koa2+mongoodb搭建了后台，前端则使用Vue+vant稍微做了一个美化的h5页面。
但是由于小组件的系统限制，无法做到实时更新，通过观察得到大概每5min更新一次。所以只能是作为一个美化桌面的工具来使用，做不到数据的实时同步。
在此期间也参考了许多文章：[网易云音乐 iOS 14 小组件实战手册](https://juejin.cn/post/6887759096506744840)对小组件开发有了更深的理解。
