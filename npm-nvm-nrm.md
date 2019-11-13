

###npm：

####1.介绍：

npm 的全称是 Node Package Manager 是 JavaScript 世界的包管理工具,并且是 Node.js 平台的默认包管理工具。通过 npm 可以安装、共享、分发代码,管理项目依赖关系。

常用命令：

npm install 安装模块

npm uninstall 卸载模块

npm update 更新模块

npm outdated 检查模块是否已经过时

npm ls 查看安装的模块

npm init 在项目中引导创建一个package.json文件

npm help 查看某条命令的详细帮助

npm root 查看包的安装路径

npm config 管理npm的配置路径

npm cache 管理模块的缓存

npm start 启动模块

npm stop 停止模块

npm restart 重新启动模块

npm test 测试模块

npm version 查看模块版本

npm view 查看模块的注册信息

npm adduser  用户登录

npm publish 发布模块

npm access 在发布的包上设置访问级别

npm package.json的语法

####2.使用淘宝的cpm代替npm

> 淘宝为我们搭建了一个国内的npm服务器，它目前是每隔10分钟将国外npm仓库的所有内容“搬运”回国内的服务器上，这样我们直接访问淘宝的国内服务器就可以了，它的地址是：https://registry.npm.taobao.org

####使用方法：

#### 第一种：直接安装cnpm

安装淘宝提供的cnpm，并更改服务器地址为淘宝的国内地址，
命令：``` npm install -g cnpm --registry=https://registry.npm.taobao.org ```，以后安装直接采用```cpm```替代```npm```，
例如原生npm命令为：```npm install uniq --save```，cnpm命令为：```cnpm install uniq --save```

#### 第二种：替换npm仓库地址为淘宝镜像地址（推荐）

命令：```npm config set registry https://registry.npm.taobao.org```，
查看是否更改成功：```npm config get registry ```，以后安装时，依然用npm命令，但是实际是从淘宝国内服务器下载的



###nvm：

####介绍：

在开发中，有时候对node的版本有要求，有时候需要切换到指定的node版本来重现问题等。遇到这种需求的时候，我们需要能够灵活的切换node版本。nvm就是为解决这个问题而产生的，他可以方便的在同一台设备上进行多个node版本之间切换

常用命令：

下载 nvm 包 地址：[nvm-windows下载](https://github.com/coreybutler/nvm-windows/releases)，我们选择第一个：nvm-noinstall.zip 下载完成后解压到一个地方，比如: C:\dev\nvm 里面的文件列表是这样的：elevate.cmd、elevate.vbs、install.cmd、LICENSE、nvm.exe

nvm install ## 安装指定版本，可模糊安装，如：安装v6.2.0，既可nvm install v6.2.0，又可nvm install 6.2

nvm uninstall ## 删除已安装的指定版本，语法与install类似

nvm use ## 切换使用指定的版本node

nvm ls ## 列出所有安装的版本

nvm ls-remote ## 列出所以远程服务器的版本（官方node version list）

nvm current ## 显示当前的版本

nvm alias ## 给不同的版本号添加别名

nvm unalias ## 删除已定义的别名

nvm reinstall-packages ## 在当前版本node环境下，重新全局安装指定版本号的npm包

ps：nvm 不支持 Windows，但是有替代品，也就是nvm-windows

####1、nvm是什么

​    nvm全名node.js version management，顾名思义是一个nodejs的版本管理工具。通过它可以安装和切换不同版本的nodejs。下面列出下载、安装及使用方法。

####2、下载

​    可在[点此在github](https://github.com/coreybutler/nvm-windows/releases)上下载最新版本,本次下载安装的是windows版本。打开网址我们可以看到有两个版本：

- nvm-noinstall.zip：绿色免安装版，但使用时需进行配置。
- nvm-setup.zip：安装版，推荐使用

####3、安装

​    本次演示的是安装版。

   1、双击安装文件 nvm-setup.exe

​    ![img](https://img2018.cnblogs.com/blog/775046/201904/775046-20190411160657751-1529010875.png)

​    2、选择nvm安装路径

​    ![img](https://img2018.cnblogs.com/blog/775046/201904/775046-20190411160816834-99504468.png)

​    3、选择nodejs路径

​    ![img](https://img2018.cnblogs.com/blog/775046/201904/775046-20190411161045308-1947410693.png)

​    4、确认安装即可

​      ![img](https://img2018.cnblogs.com/blog/775046/201904/775046-20190411171705646-891139870.png)

​    5、安装完确认

​    打开CMD，输入命令 nvm ，安装成功则如下显示。可以看到里面列出了各种命令，本节最后会列出这些命令的中文示意。

![img](https://img2018.cnblogs.com/blog/775046/201904/775046-20190411172641876-1326770838.png)

修改settings.txt
在你安装的目录下找到settings.txt文件，打开后加上
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/

####4、安装/管理nodejs

​    1、查看本地安装的所有版本；有可选参数available，显示所有可下载的版本。

```
nvm list [available]
```

​    2、安装，命令中的版本号可自定义，具体参考命令1查询出来的列表

```
nvm install 11.13.0
```

   3、使用特定版本

```
nvm use 11.13.0
```

​    4、卸载

```
nvm uninstall 11.13.0
```

####5、命令提示

1. nvm arch ：显示node是运行在32位还是64位。
2. nvm install <version> [arch] ：安装node， version是特定版本也可以是最新稳定版本latest。可选参数arch指定安装32位还是64位版本，默认是系统位数。可以添加--insecure绕过远程服务器的SSL。
3. nvm list [available] ：显示已安装的列表。可选参数available，显示可安装的所有版本。list可简化为ls。
4. nvm on ：开启node.js版本管理。
5. nvm off ：关闭node.js版本管理。
6. nvm proxy [url] ：设置下载代理。不加可选参数url，显示当前代理。将url设置为none则移除代理。
7. nvm node_mirror [url] ：设置node镜像。默认是https://nodejs.org/dist/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
8. nvm npm_mirror [url] ：设置npm镜像。https://github.com/npm/cli/archive/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。
9. nvm uninstall <version> ：卸载指定版本node。
10. nvm use [version] [arch] ：使用制定版本node。可指定32/64位。
11. nvm root [path] ：设置存储不同版本node的目录。如果未设置，默认使用当前目录。
12. nvm version ：显示nvm版本。version可简化为v。

####6、总结

​    本节列出node.js版本管理工具nvm的安装及使用，需要注意的是安装路径最好不要出现中文和空格。

 

###nrm：

####介绍：

nrm(npm registry manager )是npm 资源管理器，允许你快速切换npm 源

常用命令：

npm install -g nrm  安装

nrm ls  列出可用的源

nrm use taobao 选择国内淘宝的源

nrm test npm 测试速度

nrm add taobao http://192.168.10.127:8081/repository/npm-public/  添加源

nrm del  taobao删除对应的源


npx：
介绍：

npm v5.2.0 引入的一条命令（npx），npx 会帮你执行依赖包里的二进制文件。引入这个命令的目的是为了提升开发者使用包内提供的命令行工具的体验。全局安装 parcel，但有时不同项目使用不同版本，不允许使用全局包，只能考虑下面一些方法。使用 npm scripts，在 package.json 加一个 script ,将 node_modules 的可执行目录加到 PATH 中.指定可执行命令路径。当我们执行 npx parcel index.html 时，会自动去./node_modules/.bin 目录下搜索。


cnpm：
介绍：

因为npm安装插件是从国外服务器下载，受网络影响大，可能出现异常，所以我们乐于分享的淘宝团队干了这事。来自官网：“这是一个完整 npmjs.org 镜像，你可以用此代替官方版本(只读，不能发布自己的包或注册用户)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。”

安装：

npm install cnpm -g --registry=https://registry.npm.taobao.org

注意：安装完后最好查看其版本号cnpm -v或关闭命令提示符重新打开，安装完直接使用有可能会出现错误 

PS：cnpm跟npm用法完全一致，只是在执行命令时将npm改为cnpm。

 

由于网络原因，npm 在国内使用比较慢，所以建议切换 npm 源到国内镜像或者使用cnpm。

有两种比较方便的方式切换您的 npm 源：（ps：如果您的node版本太低可能会升级失败哦）

1.nrm：

安装：

``` npm install -g nrm```
查看所有可用源：

nrm ls
* npm -----  https://registry.npmjs.org/
  cnpm ----  http://r.cnpmjs.org/
  taobao --  https://registry.npm.taobao.org/
  nj ------  https://registry.nodejitsu.com/
  rednpm -- http://registry.mirror.cqupt.edu.cn
  skimdb -- https://skimdb.npmjs.com/registry
  切换源：（建议更换为淘宝的）

nrm use taobao    切换源

nrm del  taobao   删除对应的源（如果不想用了就可以删除它）


2.cnpm：

安装：

npm install -g cnpm --registry=https://registry.npm.taobao.org




