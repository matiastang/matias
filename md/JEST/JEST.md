<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-01 10:13:18
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-01 14:54:56
 * @Description: file content
-->
# JEST

[JEST 中文文档](https://jestjs.io/docs/zh-Hans/getting-started.html)
[vscode-jest](https://github.com/jest-community/vscode-jest/blob/master/README.md#troubleshooting)

## 安装jest

1. 全局安装（安装了可以在命令行使用`jest`命令）
```
$ npm i jest --global
```

2. 安装开发包

```
$ npm i jest ts-jest @types/jest --save-dev
```

3. 创建配置文件
```
$ jest --init
```
4. 在`package.json`中添加脚本
```js
"scripts": {
    ...
    "test": "jest"
},
```
5. 编写脚本

创建`*.test.js`文件编写测试

6. 执行测试脚本
```
$ npm run test
```

## Jest调试

[使用create-react-app调试jest单元测试不会在VSCode中命中断点](https://cloud.tencent.com/developer/ask/208645)
[react jest](https://cloud.tencent.com/developer/ask/208645)
[Getting Started](https://jestjs.io/docs/zh-Hans/getting-started)
[使用VSCode调试Jest](https://www.cnblogs.com/samwu/p/9677562.html)

## 错误处理

### Error: Jest: 'ts-node' is required for the TypeScript configuration files. Make sure it is installed

安装`ts-node`
```
$ npm i ts-node --save-dev
```

### ReferenceError: globalThis is not defined

### Matches multiple schemas when only one must validate.

[VSC 安装 Google Chrome Debugger 后出现Matches multiple schemas when only one must validate node 错误的解决方法](https://blog.csdn.net/oh_futrue/article/details/104771914)