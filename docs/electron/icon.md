

在打包electron应用程序的时候，如果没有配置icon，那么打出来的包图标就会是默认的。下面介绍一下如何创建自己的个性化图标。

### 设计图标

这里我用到了sketch，没有app的可以自行下载。

1. 新建一个文档

   创建一个宽高都为512的画板，画板内创建矩形。调整圆角，设置填充色。这里我用到了iconfont里面的图标，调整好比例。（不是专业设计师，能看就行）

   ![sketch](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWt2d3EwMDNnajMwdm8wajI3N2suanBn?x-oss-process=image/format,png)

   设计完成后就可以导出了。

2. 导出

   ![导出](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWt3MGc1MTc3ajMwdm8wajJqdWkuanBn?x-oss-process=image/format,png)

   选中画板，点击导出。导出png格式的文件即可。

3. 转换图标格式

   png格式是无法作为图标来使用的。mac上需要icns，win上需要ico格式的图标，所以需要把生成的png 图片转换成我们需要的格式。这我用到了iconSlate这个软件，当然也可以使用在线转换的网站。

   ![iconSlate](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWt3M3preXF3ajMwbTcwY2cwdzQuanBn?x-oss-process=image/format,png)

   选中png图像后可以选择导出的格式。

   ![选择格式](https://imgconvert.csdnimg.cn/aHR0cHM6Ly90dmExLnNpbmFpbWcuY24vbGFyZ2UvMDA3UzhaSWxseTFnZWt3NHhycmxvajMwaDAwZnV0OXcuanBn?x-oss-process=image/format,png)

   这样导出后就可以在electron图标配置里面引用了。
   ### 引用
   根据你选择的打包工具直接在项目中引用即可
   例：`"package": "electron-packager ./ Clipboard --win32  --out ./outapp --overwrite --icon=./icons/cb.ico --asar --app-version=1.0.0"`

