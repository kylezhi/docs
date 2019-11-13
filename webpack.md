

## 配置 4.0 +

## 使用webpack
初始化package.json
```
npm init -y
```
 - 全局安装
 ```js
npm install webpack -g
 ```
 - 本地安装
 ```js
 npm install webpack webpack-cli -D
 ```
 ## 在webpack中所有文件都是模块
  - js模块 模块化(AMD CMD es6Module Commonjs)

## 直接允许webpack
会执行node_modules对应的bin下的webpack.cmd
```
npx webpack
```


- 为了优化前端工程, 我们通常会将静态文件压缩,减少带宽占用; 将静态文件合并,减少http请求, webpack可以轻易实现静态文件的压缩合并以及打包的功能, 除此之外, webpack还支持众多的loader插件, 通过loader插件可实现众多类型(如vue, less, jpg, css)资源的打包
- webpack的文档写的相当出色, 为了方便读者学习, 下面每一类配置的注释里, 都附上了参考的原文档地址, 如果以后配置更新了,也方便查看更新的文档
- 如果不想自己配置, 可以直接拷贝最后的配置文档到自己的项目中, 所有的案例资源附在了文章末尾, 欢迎下载学习

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-b0308f5eec5d94da.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> Webpack

##npm -S -D -g i 有什么区别

```
npm i module_name  -S  = >  npm install module_name --save    写入到 dependencies 对象

npm i module_name  -D  => npm install module_name --save-dev   写入到 devDependencies 对象

npm i module_name  -g  全局安装
```

  i 是install 的简写

## 新建项目start-webpack, 初始化npm

```
mkdir start-webpack
cd start-webpack
npm init -y

```

- 初始化后, npm自动创建npm配置文件

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-1aa244068d7605cd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 初始化

## 通过npm, 安装webpack

```
npm install -D webpack
# webpack4.0 需要 额外安装webpack-cli
npm install -D webpack-cli

```

- 这里的`-D`表示只在开发阶段使用webpack, 最终打包上线的项目并不需要webpack

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-a84c74630f7b018b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 安装后

## 手动建立webpack配置文件`webpack.config.js`

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-bc37b2779a02846f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> webpack.config.js

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-c387d2eb61247736.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 创建四个文件

## 配置`package.json`,自定义webpack打包命令 [官方参考](https://link.jianshu.com?t=https%3A%2F%2Fwebpack.js.org%2Fguides%2Fgetting-started%2F)

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-ed769bd510b77a3a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 官方参考 https://webpack.js.org/guides/getting-started/
>
> 
>
> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-9c31d0a8ceb639ad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> build

- 运行命令`npm run webpack`, 进行打包, 获得 `./dist/bundle.js`

```
npm run webpack

```

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-27d95edd30d9d42b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 打包文件

- 测试打包效果

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-2bb6291fd131caba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 打包成功

## 静态文件打包(以css, 图片为例)

```
# 解决html的输出到dist  参考: https://webpack.js.org/guides/output-management/
npm install -D html-webpack-plugin
# 增加对css的支持 参考: https://webpack.js.org/guides/asset-management/#loading-css
npm install -D style-loader css-loader
# 增加对图片的支持 参考: https://webpack.js.org/guides/asset-management/#loading-images
npm install -D url-loader file-loader

```

## 支持less转义打包

```
# 安装 less-loader less 参考:https://webpack.js.org/loaders/less-loader/ 
npm install -D less-loader less

```

##支持sass转义打包

```js
npm i sass-loader node-sass -D

```



## 支持es6语法转义

```
# es6语法转义到es5 参考: https://webpack.js.org/loaders/babel-loader/
npm i babel-loader @babel/core @babel/preset-env
npm i @babel/plugin-transform-runtime --save-dev
npm i @babel/runtime --save

# 使用polyfill, 将es6的api实现出来 参考: https://babeljs.io/docs/usage/polyfill/
npm i -D babel-polyfill


#解决Webpack中提示syntax 'classProperties' isn't currently enabled的错误
npm i -D @babel/plugin-proposal-class-properties
#options: {
#       plugins: ['@babel/plugin-proposal-class-properties']
#         }
#       },



```

## 加载使用第三方包 (项目优化方案)

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-ceefebeed813e115.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 单独加载第三方包

```
# 如果将vue打包到bundle.js会增大bundle.js的体积, 所以我们配置使用全局的第三方包, 参考: https://webpack.js.org/configuration/externals/
npm install -S vue

```

## 支持vue.js打包

```
# 支持vue单文件组件加载, 参考:https://vue-loader.vuejs.org/guide/
npm i -D vue-loader vue-template-compiler

```

## 支持自动打包, 支持热重载

> 存即生效,无需刷新更新数据
>

```
# 自动打包工具  参考: https://webpack.js.org/guides/development/
npm install -D webpack-dev-server
# 支持热重载(vue子组件可无刷新更新数据), 参考: https://webpack.js.org/guides/hot-module-replacement/#enabling-hmr

```

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-3ddeaea7c39d091e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 发包目录
>
> 
>
> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-b10edd3db1661f71.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 最终项目结构

- 发包命令: `npm install --production`

> 
>
> ![img](http://upload-images.jianshu.io/upload_images/3203841-e83ccc616b58731d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
>
> 生产环境目录

------

## 最终webpack.config.js配置文件信息:

```js
const path = require('path');
// 导入在内存中生成 HTML 页面的 插件
// 只要是插件，都一定要 放到 plugins 节点中去
// 这个插件的两个作用：
//  1. 自动在内存中根据指定页面生成一个内存的页面
//  2. 自动，把打包好的 bundle.js 追加到页面中去
const HtmlWebpackPlugin = require('html-webpack-plugin');

const { VueLoaderPlugin } = require('vue-loader');
或者const VueLoaderPlugin = require('vue-loader/lib/plugin');

//热更新2步
const webpack = require('webpack');

module.exports = {

    // 设置垫脚片,设置js入口
    entry: ['babel-polyfill', './src/index.js'],
    // 使用开发服务器, 将服务运行在dist目录中(其实是虚拟于内存中的)
    // 为了解决第三方包的路径问题, 我们将'./dist'改为'./'
    devServer: {
        // 设置虚拟目录所在位置
        // contentBase: './dist'
        contentBase: path.join(__dirname, "./"),
        // 自动压缩输出的文件
        compress: true,
        // 测试端口为 9000
        port: 9000,
        // 热更新组件1步
        hot: true
    },
    // 解决index.html输出到dist的问题
    plugins: [
        new htmlWebpackPlugin({
      		template: path.join(__dirname, './src/index.html'), // 指定模板文件路径
      		filename: 'index.html' // 设置生成的内存页面的名称
   		})
        new VueLoaderPlugin(),
        new webpack.NamedModulesPlugin(),
      	//热更新3步
        new webpack.HotModuleReplacementPlugin() 
    ],
    // 单独 加载使用第三方包
    externals: {
        jquery: 'jQuery',
        vue: 'Vue'
    },
    // 设置 js 输出位置
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },
    module: {
        rules: [
            // 解决加载css资源
            { test: /\.css$/, use: ['style-loader', 'css-loader'] },
          	// 处理 less 文件的 loader
         	{ test: /\.less$/, use: ['style-loader', 'css-loader', 'less-loader'] },
          	// 配置处理 .scss 文件的 第三方 loader 规则
          	{ test: /\.scss$/, use: ['style-loader', 'css-loader', 'sass-loader'] },
           	// 处理 图片路径的 loader
            { test: /\.(jpg|png|gif|bmp|jpeg)$/, use: 'url-loader?limit=7631&name=[hash:8]-[name].[ext]' }, 
          
            // 解决es6转为es5
            {
                test: /\.js$/,
                exclude: /(node_modules|bower_components)/,
                use: {
                    loader: 'babel-loader',
                }
            },
          	
       
            // 支持vue的加载
            {
                test: /\.vue$/,
                loader: 'vue-loader'
            }
        ]
    }
};

```

## .babelsc

```js
{
    "presets": ["@babel/preset-env"],
    "plugins": [
        "@babel/plugin-proposal-class-properties",
        "@babel/plugin-transform-runtime",
        
    ]
}
```





## 最终package.json

```js
{
  "name": "webpacks",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev": "webpack-dev-server --open --contentBase src --hot --inline --port 5000"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@babel/plugin-proposal-class-properties": "^7.3.3",
    "@babel/plugin-transform-runtime": "^7.2.0",
    "babel-polyfill": "^6.26.0",
    "css-loader": "^2.1.0",
    "file-loader": "^3.0.1",
    "html-webpack-plugin": "^3.2.0",
    "less": "^3.9.0",
    "less-loader": "^4.1.0",
    "node-sass": "^4.11.0",
    "sass-loader": "^7.1.0",
    "style-loader": "^0.23.1",
    "url-loader": "^1.1.2",
    "vue-loader": "^15.6.3",
    "vue-router": "^3.0.2",
    "vue-template-compiler": "^2.6.6",
    "webpack": "^4.29.5",
    "webpack-cli": "^3.2.3",
    "webpack-dev-server": "^3.1.14"
  },
  "dependencies": {
    "@babel/core": "^7.3.3",
    "@babel/plugin-transform-object-assign": "^7.2.0",
    "@babel/preset-env": "^7.3.1",
    "@babel/runtime": "^7.3.1",
    "babel-loader": "^8.0.5",
    "jquery": "^3.3.1",
    "vue": "^2.6.6"
  }
}
```

