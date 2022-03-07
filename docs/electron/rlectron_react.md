

## 创建react项目

按照官网步骤进行操作即可

## 引入electron

__注意:引入electron的时候可能会因为网络原因导致失败，建议替换成国内源__

``npm config set ELECTRON_MIRROR=https://npm.taobao.org/mirrors/electron/``

使用yarn将npm换为yarn即可

## 创建main.js

可以参照electron官方示例。在根目录下创建main.js

```js
// Modules to control application life and create native browser window
const {app, BrowserWindow} = require('electron')
const path = require('path')


function createWindow () {
    // Create the browser window.
    const mainWindow = new BrowserWindow({
        width: 800,
        height: 600,
        webPreferences: {
            preload: path.join(__dirname, 'preload.js'),
            nodeIntegration: true
        }
    })

    // and load the index.html of the app.
    // mainWindow.loadFile('index.html')
    mainWindow.loadURL('http://localhost:3000');


    // Open the DevTools.
    mainWindow.webContents.openDevTools()
}

app.allowRendererProcessReuse =true;

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.whenReady().then(() =>{
    console.log('qpp---whenready');
    createWindow();})

// Quit when all windows are closed.
app.on('window-all-closed', function () {
    // On macOS it is common for applications and their menu bar
    // to stay active until the user quits explicitly with Cmd + Q
    console.log('window-all-closed');
    if (process.platform !== 'darwin') app.quit()
})

app.on('activate', function () {
    // On macOS it's common to re-create a window in the app when the
    // dock icon is clicked and there are no other windows open.
    if (BrowserWindow.getAllWindows().length === 0) createWindow()
})

// In this file you can include the rest of your app's specific main process
// code. You can also put them in separate files and require them here.

```



注意配置![main.js配置](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZThoZnBzNmo3ajMwZHcwOWkwdHQuanBn?x-oss-process=image/format,png)

因为我们是加载的react生成的页面，并不是静态页面，所以要将第二处的loadFile换成loadURL。

第一处配置同样不要忘了加。否则在render页面会提示node找不到的错误。

react项目文件引入electron，注意使用方式。

![react页面引用electron](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZThobmJoZWFyajMwZ3UwOW1qc2cuanBn?x-oss-process=image/format,png)

## 修改package.json

![package.json](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZThoaTY3MHFmajMwZ3QwNm53ZmUuanBn?x-oss-process=image/format,png)

添加main.js以及启动指令。启动electron时输入``yarn electron``即可启动electron。

这里我使用了nodemon监听文件改变，不用每次都手动重启electron。有兴趣的可以使用，方便了许多。

------

所有操作完成后，可以启动react项目以后启动electron，就可以在electron窗口看到效果了。