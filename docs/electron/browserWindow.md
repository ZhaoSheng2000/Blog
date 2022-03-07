

# electron之[BrowserWindow](https://www.electronjs.org/docs/api/browser-window#browserwindow)的常用设置

在设置完main.js以后就可以在electron生成的window里面利用react+antd显示业务效果了。

创建BrowserWindow需要在main.js也就是主进程里面创建。关于BrowserWindow的相关属性可以参考官网[BrowserWindow](https://www.electronjs.org/docs/api/browser-window#browserwindow)。

这里主要记录的是如何实现在点击关窗口的闭按钮时隐藏浏览器窗口而不是真正的关闭。

## 监听窗口关闭事件



#### 事件： 'close'

返回:

- `event` Event

在窗口要关闭的时候触发。

这是官网的实例事件。我们可以利用`e.preventDefault();`来阻止关闭事件的发生并隐藏窗体。

```js
  mainWindow.on('close', e => {
        mainWindow.hide();
        e.preventDefault();
    })

```

那么想要退出应用的时候如何真正的退出呢？可以通过快捷键以及菜单项实现。下一篇介绍如何添加系统托盘，快捷键的绑定以及系统托盘与快捷键的关联。

