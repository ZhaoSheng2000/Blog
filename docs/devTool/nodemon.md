
>nodemon是一种工具，可以自动检测到目录中的文件更改时通过重新启动应用程序来调试基于node.js的应用程序。

在我使用react+antd开发electron桌面应用的时候总是需要重启electron .来查看修改效果，每次都需要输入两次指令，很不方便。使用nodemon可以监听文件变化，避免每次重复输入指令重启electron。
### 安装
``
npm install -g nodemon
npm install --save-dev nodemon
``
### 使用

在我的项目里是这么使用的：
在package.json配置
![配置](https://img-blog.csdnimg.cn/20210428131939109.png)
这样就可以监听其他文件的改变，改变以后执行electron . 命令
### 文档
[nodemon](https://www.npmjs.com/package/nodemon)