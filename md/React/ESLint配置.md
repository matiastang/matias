<!--
 * @Author: tangdaoyong
 * @Date: 2020-11-25 09:45:57
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-11-25 10:41:51
 * @Description: file content
-->
# ESLint配置

[官网](https://eslint.bootcss.com/)
[VSCode 使用 ESLint + Prettier 来统一 JS 代码](https://www.cnblogs.com/xjnotxj/p/10828183.html)
[vscode eslint](https://blog.csdn.net/weixin_34289744/article/details/91370709)

## 安装
```
$ npm i eslint eslint-loader eslint-plugin-html eslint-friendly-formatter eslint-plugin-react --save-dev
```
## 在命令行中执行 `eslint` 命令，生成 `.eslintrc.js`
```
$ node_modules/.bin/eslint --init
```
```js
#您想如何使用ESLint?
? How would you like to use ESLint? (Use arrow keys)
> To check syntax, find problems, and enforce code style

#您的项目使用什么类型的模块?
? What type of modules does your project use? (Use arrow keys)
> JavaScript modules (import/export)

#您的项目使用哪个框架?
? Which framework does your project use? (Use arrow keys)
> React

#您的项目使用 typescript 吗？
? Does your project use TypeScript? (y/N) > n

#你的代码在哪里运行?(按<space>选择，<a>切换所有，<i>反转选择)
? Where does your code run? (Press <space> to select, <a> to toggle all, <i> to invert selection)
>(*) Browser
#您想如何为您的项目定义一个样式? 选择哪个都行
? How would you like to define a style for your project? (Use arrow keys)
> Answer questions about your style #自定义格式
#代码格式化风格？
? What format do you want your config file to be in? > JavaScript
#用tab还是空格
? What style of indentation do you use? > Spaces
#字符串用单引号还是双引号？
? What quotes do you use for strings? > Single
#行结束符
? What line endings do you use? > Unix
#需要分号吗？
? Do you require semicolons? (Y/n) > y
```
```js
✔ How would you like to use ESLint? · style
✔ What type of modules does your project use? · esm
✔ Which framework does your project use? · react
✔ Does your project use TypeScript? · No / Yes
✔ Where does your code run? · browser
✔ How would you like to define a style for your project? · prompt
✔ What format do you want your config file to be in? · JavaScript
✔ What style of indentation do you use? · tab
✔ What quotes do you use for strings? · single
✔ What line endings do you use? · unix
✔ Do you require semicolons? · No / Yes
```
## 修改`.eslintrc.js`配置
```js
    'env': {
		'amd': true, //表示使用amd模块规范，支持 require
		'node': true, //支持node
		'browser': true,
		'es2021': true
	},
```
## `webpack.config.js`中添加规则
```js
{
    test: /\.js|jsx$/,            //匹配文件
    exclude: /node_modules/,      //排除文件夹
    use: [
        { loader: 'babel-loader' }, // babel 加载器
        { loader: 'eslint-loader',  // eslint 加载器
        options: {                // eslint 选项
            enforce: 'pre',         //在加载前执行
            fix: true,              //自动修复
            include: [path.resolve(__dirname, 'src')], //指定检查的目录
            formatter: require('eslint-friendly-formatter') // 指定错误报告的格式规范
        }
        },
    ]
},
```
## `package.json`中配置命令
```
"scripts": {
    "lint": "eslint --ext .js --ext .ts --ext .jsx --ext .tsx src/",
},
```
`--ext`表示要解析的文件，最后接上文件的路径。