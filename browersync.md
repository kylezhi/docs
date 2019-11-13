**相关链接：**
[Browsersync官网](https://link.jianshu.com?t=https://browsersync.io)
[Browsersync中文网](https://link.jianshu.com?t=http://www.browsersync.cn/)

1. 下载安装 [nodejs](https://link.jianshu.com?t=https://nodejs.org/en/)
2. 命令行窗口 ( 全局安装 browsersync )：
   `npm install -g browser-sync`
3. 在 **项目文件夹** 内同时按住 **shift** 和 **右击**，可以看到 `在此处打开命令窗口`, 点击打开命令行窗口
4. 在命令行窗口内输入以下命令
   `browser-sync start --server --files "**"`
   ( 启动 Browsersync，--server **默认以当前目录为服务器根目录**，--files 后面要记得空一格再写要监听的文件，`**`表示监听所有文件，一旦文件修改浏览器自动刷新，适合小型项目 )
5. 最实用的两大功能：代码文件修改并保存后浏览器页面自动刷新，同一局域网下手机（连 WIFI）可进行页面的联调。

**PS**：下面内容的 1-3 部分是官网工具介绍的中文翻译，仔细阅读的话可对该工具有更深入的了解，也可略过直接跳到第 4 部分进行阅读。

## 1. 概述

Browsersync是您不可或缺的测试工具。
针对越来越多的网站页面、各种设备和多个浏览器，我们在测试代码上花费的时间越来越多。从实时刷新页面、URL发布到表单拷贝、点击事件镜像，Browsersync 减少了重复的手动操作，就像是多出了一双手一样。在UI界面或命令行中自定义一系列的同步设置，创建一个个性化的测试环境。Browsersync 很容易集成到您的web平台、构建工具和其他 Node.js 项目中。

## 2. 主要功能

- Browsersync 能让浏览器实时、快速响应您的文件更改（html、js、css、sass、less等）并自动刷新页面。更重要的是 Browsersync 可以同时在PC、平板、手机等设备下进行调试。

  ​

  ![img](http://upload-images.jianshu.io/upload_images/448830-7c0b1b5a51f14e39.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/500/format/webp)

  Browsersync

  ​

  图片来自 Browsersync 中文官网

  ​

- 在一个浏览器中滚动页面、点击等行为也会同步到其他浏览器和设备中，这一切还可以通过可视化界面来控制。

  ​

  ![img](http://upload-images.jianshu.io/upload_images/448830-edff2e080c081680.gif?imageMogr2/auto-orient/strip%7CimageView2/2/w/480/format/webp)

  Browsersync

  ​

  图片来自 Browsersync 中文官网

  ​

## 3. 所有特性

- **Install and run anywhere**
  基于Node.js构建，支持 Windows, MacOS 和 Linux 平台。5分钟快速搭建。
- **Free to run and reuse**
  Browsersync 是一个开源项目，可根据 Apache 2.0 许可使用和修改。
- **Build-tool compatible**
  可以轻松集成到自动化工具中，如 Grunt 和 Gulp，或其他 Node 项目中。
- **Network Throttle**
  在网络连接速度慢的情况下也可以测试你的网页，就算设备连接的是 Wifi。
- **Interaction sync**
  当你测试时，你对页面的滚动、点击、刷新和表单操作都将在所有浏览器中同步显示。
- **File sync**
  当你修改 HTML, CSS, 图片或其他项目文件时，浏览器都会自动刷新
- **UI or CLI control**
  可以使用基于浏览器的 UI 界面来进行快速操作，也可以使用命令行工具。
- **Sync customisation**
  切换个人同步设置来创建你喜欢的测试环境。
- **URL history**
  记录你测试过的 URL，只要一键就能允许你重新在所有设备上打开该页面。

## 4. 5分钟快速入门

1. 安装 Node.js
   下载地址在[这里](https://link.jianshu.com?t=https://nodejs.org/en/)。
2. 安装 BrowserSync
   **方法一**：使用 npm 安装
   打开一个终端窗口，运行以下命令:
   `npm install -g browser-sync`
   **方法二**：结合`gulpjs`或`gruntjs`构建工具使用
   在您需要构建的项目里运行下面的命令：
   `npm install --save-dev browser-sync`
   **方法一**安装完后在命令行中输入`browser-sync`，回车，会看到关于这个插件的一些使用说明。

**相关的命令行说明：**
[Browsersync 官网命令行说明](https://link.jianshu.com?t=https://browsersync.io/docs/command-line/)
[Browsersync 中文网命令行说明](https://link.jianshu.com?t=http://www.browsersync.cn/docs/command-line/)
**常用命令:**
**--files**     
File paths to watch / 后面跟要监听的文件路径
**--server**    
Run a Local server (uses your *cwd* as the web root) / 运行一个本地服务器（使用您的 *当前工作目录* 作为 Web 根目录）
**--proxy**     
Proxy an existing server / 代理一个现有的服务器
**--config**    
Specify a path to a bs-config.js file / 指定 bs-config.js peizhi文件的路径

1. 启动 BrowserSync

> **小贴士：**按住 Shift 键，右键点击文件夹，可以看到`在此处打开命令行窗口`，点击后，命令行窗口的  *当前工作目录* 即为此文件夹。

**命令行使用示例**：

```
#Server Example（服务器模式，针对静态网页）:
---------------
// Use current directory as root & watch CSS files
// BrowserSync 将以当前路径为根目录创建一个小型服务器，并提供一个URL地址来查看您的网站 & 监听 CSS 文件
在命令行窗口中运行下面命令：

    browser-sync start --server --files "css/*.css"
    
#Proxy Example（代理模式，针对已经有本地服务器的环境）:
---------------
// Proxy 'localhost:8080' & watch CSS/HTML files
// 代理地址（ip 或域名） "localhost:8080" & 监听 CSS/HTML 文件
在命令行窗口中运行下面命令：

    browser-sync start --proxy "localhost:8080" --files "*.html,css/*.css"

```

## 5. 须知

- --files 后的文件路径是相对于运行该命令的当前目录的
  `browser-sync start --server --files "css/*.css"`
- 如果您需要监听多个类型的文件，您只需要用逗号隔开
  `browser-sync start --server --files "css/*.css, *.html"`
- 如果你的文件层级比较深，您可以考虑使用 **（表示任意目录）匹配

```
//任意目录下任意 .css 或 .html 文件
browser-sync start --server --files "**/*.css, **/*.html"

//任意目录下任意 .css .js 或 .html 文件
browser-sync start --server --files "*.html, css/*.css, js/*.js"
```