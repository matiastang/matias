<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-21 11:08:20
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-21 11:27:39
 * @Description: ts引用样式
-->

# ts引用样式

# typed-css-modules

命令行生成
[typed-css-modules](https://github.com/Quramy/typed-css-modules)

# typings-for-css-modules-loader

编译时生成
[typings-for-css-modules-loader](https://github.com/Jimdo/typings-for-css-modules-loader)
`typings-for-css-modules-loader`让我们可以像使用`js`模块一样引入`css`和`scss`文件。
不过该项目不维护了，要使用需要控制，使用`@teamsupercell/typings-for-css-modules-loader`。

# @teamsupercell/typings-for-css-modules-loader

[https://github.com/TeamSupercell/typings-for-css-modules-loader](@teamsupercell/typings-for-css-modules-loader)
使用之后会生成`.scss`对应的`.scss.d.ts`文件。
```js
{
    test: /\.scss$/,
    use: [{
        loader: 'style-loader'
    }, {
        loader: '@teamsupercell/typings-for-css-modules-loader',
        // typings-for-css-modules-loader让我们可以像使用js模块一样引入css和scss文件。
        options: {
            formatter: 'prettier'
        }
    }, {
        loader: 'css-loader',
        options: {
            modules: {
                localIdentName: '[local]_[hash:base64:5]'
            },
            sourceMap: true,
            importLoaders: 2
        }
    }, {
        loader: 'sass-loader'
    }, {
        loader: 'postcss-loader'
    }]
},
```

## fork-ts-checker-webpack-plugin

[fork-ts-checker-webpack-plugin](https://github.com/TypeStrong/fork-ts-checker-webpack-plugin#plugin-hooks)
使用之后延迟检查类型
```js
const ForkTsCheckerWebpackPlugin = require('fork-ts-checker-webpack-plugin');
plugins: [
    new ForkTsCheckerWebpackPlugin()
],
module: { // 加载器
    rules: [// 规则
        {
            test: /\.tsx?$/,
            use: [{
                loader: 'babel-loader'
            }, {
                loader: 'ts-loader',
                options: {
                    // disable type checker - we will use it in fork plugin
                    transpileOnly: true
                }
            }],
            exclude: /node_modules/
        }
    ]
}
```

## 引入
在`.tsx`文件中，引用时需要使用`import styles from './point.scss';`方式引入。
`import * as styles from './point.scss';`引入样式不生效。