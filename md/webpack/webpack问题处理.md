<!--
 * @Author: tangdaoyong
 * @Date: 2021-01-11 15:50:06
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-01-11 16:01:36
 * @Description: webpack常见问题处理
-->
# webpack常见问题处理

## Error: Cannot find module 'webpack-cli/bin/config-yargs'

安装的`webpack-cli`是最新版本(4.*)，需要降版本。

1. 卸载当前的 `webpack-cli`
```
npm uninstall webpack-cli
yarn remove webpack-cli
```

2. 安装 webpack-cli 3.* 版本
```
npm install webpack-cli@3
yarn add --dev webpack-cli@^
```