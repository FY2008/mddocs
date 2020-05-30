# Electron 写第一个Gui程序

[TOC]

## 关于Electron

> **Electron** 是由 Github 开发，用HTML, CSS和JavaScript来构建跨平台应用程序的一个开源库。Electron通过将Chromium和Node.js合并到同一个运行时环境中，并将其打包为Mac，Windows和Linux系统下的应用来实现这一目的。

**Atom**编辑器是第一个用Electron来开发的跨平台应用程序，当下最热门的VSCode 也是用 Electron 技术来开发的，接下来我们使用 Electron 来搭建第一个程序 Hello,World!

我的平台：`Windows 10`，`VSCode编辑器`，`node 12.13.0`，`Electron 8.2.0`

## 第一个程序步骤

### 安装 Nodejs

这一步就不做介绍了，掠过。

### 安装 Electron 前的配置

这一步我遇到了一些问题，是因为国内的网络问题，所以需要配置镜像和一些专门针对 Electron 的配置。

这里列出我的配置文件：配置文件在 用户目录下的 `.npmrc` 文件里

```
registry=http://registry.npm.taobao.org/
prefix=D:\bin\nodejs\node_global
cache=D:\bin\nodejs\node_cache
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
phantomjs_cdnurl=http://npm.taobao.org/mirrors/phantomjs
ELECTRON_MIRROR=http://npm.taobao.org/mirrors/electron/
electron_custom_dir=8.2.0
```

配置好 `.npmrc` 文件后就可以安装 Electron 了。

从开发的角度来看, Electron application 本质上是一个 Node. js 应用程序。 与 Node.js 模块相同，应用的入口是 package.json 文件。 一个最基本的 Electron 应用一般来说会有如下的目录结构：

1. 初始化 `npm init`

   your-app/
   ├── package.json
   ├── main.js
   └── index.html

npm 会帮助你创建一个基本的 package.json 文件。 其中的 main 字段所表示的脚本为应用的启动脚本，它将会在主进程中执行。 如下片段是一个 package.json 的示例：

```json
{
	"name": "your-app",
  	"version": "0.1.0",
  	"main": "main.js"
}
```

**注意**：如果 `main` 字段没有在 `package.json` 中出现，那么 Electron 将会尝试加载 index.js 文件（就像 Node.js 自身那样）。 如果你实际开发的是一个简单的 Node 应用，那么你需要添加一个 `start` 脚本来指引 `node` 去执行当前的 package：

```json
{
  "name": "your-app",
  "version": "0.1.0",
  "main": "main.js",
  "scripts": {
    "start": "node ."
  }
}
```

把这个 Node 应用转换成一个 Electron 应用也是非常简单的，我们只不过是把 node 运行时替换成了 electron 运行时。

```json
{
  "name": "your-app",
  "version": "0.1.0",
  "main": "main.js",
  "scripts": {
    "start": "electron ."
  }
}
```

### 安装 Electron

现在，您需要安装electron。 我们推荐的安装方法是把它作为您 app 中的开发依赖项，这使您可以在不同的 app 中使用不同的 Electron 版本。 在您的app所在文件夹中运行下面的命令：

`npm install --save-dev electron`

安装完 Electron 后要做的事情就是照着 官网的 HelloWorld ! 例子程序抄写一篇测试一下。

### 开始第一个程序

这个程序主要就两个文件，一个 index.html，另一个是 main.js。index.html 就是普通的 html，主程序是有 main.js 来完成的。下面列出两个文件的代码：

**index.html**

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <title>Hello World! - https://www.z10.xin</title>
    <!-- https://electronjs.org/docs/tutorial/security#csp-meta-tag -->
    <meta http-equiv="Content-Security-Policy" content="script-src 'self' 'unsafe-inline';" />
</head>

<body>
    <h1>Hello World! - <span style="color: #c00;">https://www.z10.xin</span></h1>
    We are using node
    <script>
        document.write(process.versions.node)
    </script>, Chrome
    <script>
        document.write(process.versions.chrome)
    </script>, and Electron
    <script>
        document.write(process.versions.electron)
    </script>.
</body>

</html>
```

**main.js**

```javascript
const { app, BrowserWindow } = require('electron')

function createWindow() {
    let win = new BrowserWindow({
        width: 800,
        height: 600,
        webPreferences: {
            nodeIntegration: true
        }
    })

    win.loadFile('index.html')
}

app.whenReady().then(createWindow)
```

### 运行

`npm start`

<video id="video" controls="" preload="none">
<source id="mp4" src="Electron_helloworld.mp4" type="video/mp4">
</video>