## 快速掌握Nest Cli

项目开发离不开工程化的部分，比如创建项目、编译构建、开发时 watch 文件变动自动构建等。

Nest 项目自然也是这样，所以它在 @nestjs/cli 这个包里提供了 nest 命令。

可以直接 npx 执行，npm 会把它下载下来然后执行：

```
npx @nestjs/cli new 项目名
```
也可以安装到全局，然后执行，更推荐这种：

```
npm install -g @nestjs/cli

nest new 项目名
```
不过后者要时不时升级下版本，不然可能用它创建的项目版本不是最新的：

```
npm update -g @nestjs/cli
```

nest 命令除了可以生成整个项目外，还可以生成一些别的代码，比如 controller、service、module 等。

比如生成 module：
```
nest generate module aaa
```
当然你也可以生成 controller、service 等代码.

当然，如果是要完整生成一个模块的代码，不需要一个个生成，可以用

```
nest generate resource xxx
```
它会让你选择是哪种代码，因为 nest 支持 http、websocket、graphql、tcp 等，这里我们选择 http 的 REST 风格 api：

然后会让你选择是否生成 CRUD 代码：

选择是。

然后就会生成整个模块的 CRUD + REST api 的代码：


ZhaoSheng2000的头像
项目开发离不开工程化的部分，比如创建项目、编译构建、开发时 watch 文件变动自动构建等。

Nest 项目自然也是这样，所以它在 @nestjs/cli 这个包里提供了 nest 命令。

可以直接 npx 执行，npm 会把它下载下来然后执行：

npx @nestjs/cli new 项目名
也可以安装到全局，然后执行，更推荐这种：

npm install -g @nestjs/cli

nest new 项目名
不过后者要时不时升级下版本，不然可能用它创建的项目版本不是最新的：

npm update -g @nestjs/cli
那 nest 都提供了啥命令呢？

nest -h 看看:



有创建新项目的 nest new，有创建某些代码的 nest generate，还有编译构建的 nest build，开发模式的 nest start 等。

分别看一下：

nest new 我们用过，就是创建一个新的 nest 项目的。

它有这么几个选项：



--skip-git 和 --skip-install 很容易理解，就是跳过 git 的初始化，跳过 npm install。

--package-manager 是指定包管理器的，之前创建项目的时候会让我们选择：



指定之后，就跳过包管理器选择这步了：



--language 可以指定 typescript 和 javascript，一般我们都选择 ts，用默认的就好。

--strict 是指定 ts 的编译选项是否开启严格模式的，也就是这么 5 个选项：



默认是 false，也可以指定为 true：



这个之后需要的话再改就行。

至于 --collection 的解释，就要涉及到 nest generate 命令了：

nest 命令除了可以生成整个项目外，还可以生成一些别的代码，比如 controller、service、module 等。

比如生成 module：

nest generate module aaa


它会生成 module 的代码：



还会自动在 AppModule 里引入：



当然你也可以生成 controller、service 等代码：

nest generate controller aaa


同样，它也会更新到 module 的依赖里去。

生成 service 也是一样：



当然，如果是要完整生成一个模块的代码，不需要一个个生成，可以用

nest generate resource xxx
它会让你选择是哪种代码，因为 nest 支持 http、websocket、graphql、tcp 等，这里我们选择 http 的 REST 风格 api：



然后会让你选择是否生成 CRUD 代码：



选择是。

然后就会生成整个模块的 CRUD + REST api 的代码：





当然，它同样会自动在 AppModule 引入：



这就是 nest generate，可以快速生成各种代码：



这些代码模版的集合是在 @nestjs/schematics 这个包里定义的。

还记得 nest new 创建项目的时候有个 --collection 选项么，就是配置这个的。

不过一般我们不需要配置。

你可以在 @nestjs/schematics 里看到这些代码模版的定义：



它的实现原理很简单，就是模版引擎填充变量，打印成代码：



其中有种 application 的类型：

它生成的就是整个项目结构：





其实 nest new 的底层就是 nest generate application，只不过 nest new 额外做了 git init 和 npm install 等处理。

nest generate 也有不少选项：



--flat 和 --no-flat 是指定是否生成对应目录的：



--spec 和 --no-spec 是指定是否生成测试文件：



--skip-import 是指定不在 AppModule 里引入：



也就是不生成这部分代码：



至于 --project，这是指定生成代码在哪个子项目的，等之后用到 monorepo 项目的时候再说。

这就是 nest cli 提供的快速生成各种代码的能力，是不是还挺方便的？

然后就是 nest build 了，它是用来构建项目的:



执行 nest build，会在 dist 目录下生成编译后的代码。

同样，它也有一些选项：



--wepback 和 --tsc 是指定用什么编译，默认是 tsc 编译，也可以切换成 webpack。

这是 tsc 的编译产物：



这是 webpack 的编译产物：



tsc 不做打包、webpack 会做打包，两种方式都可以。

node 模块本来就不需要打包，但是打包成单模块能提升加载的性能。

--watch 是监听文件变动，自动 build 的。

但是 --watch 默认只是监听 ts、js 文件，加上 --watchAssets 会连别的文件一同监听变化，并输出到 dist 目录，比如 md、yml 等文件。

--path 是指定 tsc 配置文件的路径的。

那 --config 是指定什么配置文件呢？

是 nest cli 的配置文件。

刚刚我们说的那些选项都可以在 nest-cli.json 里配置：



比如 compilerOptions 里设置 webpack 为 true 就相当于 nest build --webpack，一样的效果：



webpack 设置为 false 就是用 tsc 了。

deleteOutDir 设置为 true，每次 build 都会都清空 dist 目录。

而 assets 是指定 nest build 的时候，把那些非 js、ts 文件也复制到 dist 目录下。

可以通过 include、exclude 来精确匹配，并且可以单独指定是否 watchAssets。

不过只支持 src 下文件的复制，如果是非 src 下的，可以自己写脚本复制：



然后是 generateOptions，这些就和我们 nest generate 时的 --no-spec、--no-flat 一样的效果。

比如我把 flat 设置为 false、spec 设置为 false，那再 generate 代码时就是这样的：



生成了一层目录，并且没有生成测试文件。

sourceRoot 是指定源码目录。

entryFile 是指定入口文件的名字，默认是 main。

而 $schema 是指定 nest-cli.json 的 schema，也就是可以有哪些属性的：

json.schemastore.org/nest-cli

这是一种 json schema 的规范，还是挺容易看懂的：



如果想全面了解 nest-cli.json 都有啥属性，可以看看这个 schema 定义。

最后，再来看下 nest start 命令：



可以看到每次重新 build 了，并且用 node 把 main.js 跑了起来。

它有这些选项：



--watch 是最常用的选项了，也就是改动文件之后自动重新 build：



--debug 是启动调试的 websocket 服务，用来 debug。



--exec 可以指定用什么来跑，默认是用 node 跑，你也可以切换别的 runtime。

其余选项和 nest build 一样，就不复述了。

最后还有个 nest info 命令，这个就是查看项目信息的，包括系统信息、 node、npm 和依赖版本：



### 总结
nest 在 @nestjs/cli 包里提供了 nest 命令，它可以用来做很多事情：

生成项目结构和各种代码
编译代码
监听文件变动自动编译
打印项目依赖信息
也就是这些子命令：

nest new 快速创建项目
nest generate 快速生成各种代码
nest build 使用 tsc 或者 webpack 构建代码
nest start 启动开发服务，支持 watch 和调试
nest info 打印 node、npm、nest 包的依赖版本
并且，很多选项都可以在 nest-cli.json 里配置，比如 generateOptions、compilerOptions 等。

学会用 nest cli，是学好 nest 很重要的一步。
