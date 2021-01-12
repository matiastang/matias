<!--
 * @Author: tangdaoyong
 * @Date: 2021-01-12 16:16:00
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-01-12 16:17:48
 * @Description: React 设置多个className
-->
# React 设置多个className

1. ES6 模板字符串 ``
```js
className={`title ${index === this.state.active ? 'active' : ''}`}
```
2. join('')
```js
className={["title", index === this.state.active?"active":null].join(' ')}
```
3. classnames(需要下载classnames)
```js
const classNames = require('classnames');
 
const Button = React.createClass({
  // ...
  render () {
    const btnClass = classNames({
      btn: true,
      'btn-pressed': this.state.isPressed,
      'btn-over': !this.state.isPressed && this.state.isHovered
    });
    return <button className={btnClass}>{this.props.label}</button>;
  }
});
```