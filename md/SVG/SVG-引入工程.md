<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-17 16:54:16
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-17 17:25:22
 * @Description: 引入SVG
-->
# SVG

[@svgr/webpack](https://www.npmjs.com/package/@svgr/webpack)
[在react中使用svg的各种方法总结](https://www.php.cn/html5-tutorial-407403.html)

## 引入SVG

### 直接使用`svg`

```ts
function SVG() {

    return (
        <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
            <circle cx="100" cy="50" r="40" stroke="black"
                stroke-width="2" fill="red" />
        </svg>
    );
}
```

### TypeScript + Webpack

在`TS`直接使用`.svg`格式文件时会提示错误，如下：
```ts
import htllSVG from '../resource/hello.svg';
// Cannot find module '../resource/hello.svg' or its corresponding type declarations.ts(2307)
```

#### 使用`require`引入
```ts
const helloURL = require('../resource/hello.svg');// 引入路径使用

function SVG() {

    return (
        <>
            <embed src={ helloURL } type="image/svg+html"></embed>
            <object data={ helloURL } type="image/svg+html"></object>
            <iframe src={ helloURL } ></iframe>
        </>
    );
}
```
#### 使用`Webpack loader`引入`SVG`组件（构建前转换）

typescript-react-svg-icon-generator, 需要我们有一条前置命令去把svg做转换.
```js
// svg-generator.js
const generator = require('typescript-react-svg-icon-generator')

const config = {
    svgDir: './svg/',
    destination: './Icon/index.tsx'
}

generator(config)
```
执行转换：
```
node ./svg-generator.js
```
使用：
```ts
import HelloSVG from '../resource/hello.svg';// 引用为React组件

function SVG() {

    return (
        <HelloSVG />
    );
}
```

#### 使用`Webpack loader`引入`SVG`组件（构建时转换）

需要使用`Webpack loader`如：[@svgr/webpack](https://www.npmjs.com/package/@svgr/webpack)

```ts
import HelloSVG from '../resource/hello.svg';// 引用为React组件

function SVG() {

    return (
        <HelloSVG />
    );
}
```
1. 安装`@svgr/webpack`
```
// npm
npm install @svgr/webpack --save-dev
// yarn
yarn add @svgr/webpack --dev
```

2. 安装`@svgr/webpack`的依赖，如果安装了就不用安装了。
```
yarn add @babel/core @babel/plugin-transform-react-constant-elements @babel/preset-env @babel/preset-react @svgr/core @svgr/plugin-jsx @svgr/plugin-svgo loader-utils --dev
```

3. 配置`webpack`
```js
resolve: {
    extensions: ['.svg']
},
{
    test: /\.svg$/,
    use: ['@svgr/webpack']
},
```
**注意**如果`svg`文件的存放是和`jpg`以及`png`等图片同一目录的，则需要在`url-loader`或`file-loader`的配置中使用`exclude`去除`svg`的匹配，因为如果不去除会导致`svg`经过`hash`指纹重命名之后，`loader`找不到`svg`文件，进而导致报错。

4. `TS`全局声明

* 创建`globals.d.ts`文件，名字可以随便取，后缀为`.d.ts`就可以。
```ts
// 全局声明svg component定义
declare interface SvgrComponent extends React.FunctionComponent<React.SVGAttributes<SVGAElement>> {}

declare module '*.svg' {
    const content: SvgrComponent;
    // const content: ReactComponent;
    export default content;
}
```
* 配置`tsconfig.json`
```json
"include": [
    "src",
    "globals.d.ts"//配置的.d.ts文件
]
```
5. 使用`.svg`
```ts
import HelloSVG from '../resource/hello.svg';// 引用为React组件

function SVG() {

    return (
        <HelloSVG />
    );
}
```
这个方案好处不仅体现在构建时转换, 更重要的是它完全继承了SVGAttributes, 不需要额外的学习成本! 可参考项目ts-react-webpack4, 或脚手架steamer-react-ts

## 扩展

* 还有react-svg, svg-react-loader等同样是以类似的方式实现的.
* `Vue`使用的`svg-sprite-loader`没试过。
* `Typescript`中使用`.scss`参考，写的很好[CSS in Typescript](https://juejin.cn/post/6844903560056930311)