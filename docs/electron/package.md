

在所有工作完成以后（react页面开发完成，页面已经build），就需要对我们的项目进行打包。

------

## 打包前的配置

首先要知道我们在开发的时候主进程加载的是react前端页面的本地url，这里需要换成react打包后的本地文件地址。

![url地址](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWthaHd6ZWMxajMwa2YwMWEzeXAuanBn?x-oss-process=image/format,png)

__注意：react打包以后可能会出现各种各样的的问题，这里我就遇到了一个问题。就是开发的时候页面正常显示，打包成静态文件以后点击空白，一开始以为是没有设置homepage，检查之后发现不是这里的问题。后来经过多方面排查发现路由用的是`BrowserRouter`,对应的地址必须是服务器这是存在的，所以本地文件肯定无法正常显示。换成了`HashRouter`以后问题成功解决__

这样以后可以测试一下换成静态页面electron能否正常加载，不能正常加载一般情况下是路径的问题。

## 准备打包

首先需要安装`asar`

`$ npm install -g asar`

使用`asar pack` 打包

`$ asar pack your-app app.asar`这样做的目的是为了减小打包后的文件体积。关于原理可以参考官方文档。[ 使用 `asar pack` 打包](https://www.electronjs.org/docs/tutorial/application-packaging#2-%E4%BD%BF%E7%94%A8-asar-pack-%E6%89%93%E5%8C%85)

然后需要使用[`electron-packager`](https://github.com/electron/electron-packager),、[`electron-forge`](https://github.com/electron-userland/electron-forge)和[`electron-builder`](https://github.com/electron-userland/electron-builder)中的一个，这里我使用的是`electron-packager`,下面也会为大家介绍我是如何使用的。

1. __全局安装__

   ```
   npm install electron-packager -g
   ```

2. 编写打包命令

   ![命令](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWtheHliMXpvajMwbWcwMjVkZzUuanBn?x-oss-process=image/format,png)

`electron-packager <sourcedir> <appname> --platform=<platform> --arch=<arch> [optional flags...]`

具体参数见[electron-packager](<https://github.com/electron/electron-packager>)

3. 执行打包命令

   `npm run package`或 `yarn package`

4. 减小包大小

   这样打包以后文件大小大概要500M左右，但是其实许多依赖我们是用不到的，就可以把用得到的留下，用不到的删掉。

   ![依赖](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWtiMmQ5MHFoajMwZWowZW4wdWsuanBn?x-oss-process=image/format,png)

   这里好多依赖都是在开发react前端页面的时候使用的，前端页面已经打包好了，所以说该删的就要删掉。（我建议先commit一份到github或者本地保留一份，以便后期开发react前端页面的时候找不到依赖）

   ![删除依赖](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWtiOWdldHJpajMwZDYwZGNqdDEuanBn?x-oss-process=image/format,png)

   这里我只留下了这两个，根据情况，留下在主进程main.js里面用到的依赖就好了。

   ------

   此时再次打包，体积就会减少到100-200M，分发起来也很方便。