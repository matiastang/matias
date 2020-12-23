# SVG动画

[SVG 动画（animate、animateTransform、animateMotion）](https://blog.csdn.net/chy555chy/article/details/53535581)

## React中的SVG动画

### svg不执行动画

1. 创建`.svg`文件
```svg
<svg width="500px" height="500px">
  <rect x="0" y="0" width="100" height="100" fill="#feac5e">
    <animate attributeName="x" from="0" to="500" dur="2s" repeatCount="indefinite" />
  </rect>
</svg>
```
2. 使用`@svgr/webpack`加载器引入组件化的`svg`组件。
```ts
import HelloSVG from '../resource/hello.svg';// 引用为React组件

function SVGBase() {

    return (
        <HelloSVG />
    );
}
```
3. 此时动画不生效

运行发现动画不生效，打开调试发现`.svg`中的`rect`被替换成了`path`，所有不执行动画。
```html
<svg width="500" height="500"><path fill="#feac5e" d="M0 0h100v100H0z"><animate attributeName="x" from="0" to="500" dur="2s" repeatCount="indefinite"></animate></path></svg>
```
应该是`@svgr/webpack`转换为组件时替换的，如果没有动画这个替换也不影响。不知道还会不会有其他元素的替换！也不知道这个替换是为了干嘛，提升性能吗？有空可以研究一下。

4. 直接引入可以执行动画

如下直接在`tsx`中写`svg`，和路径引入动画可以执行。所有
```tsx

function SVGBase() {

    return (
        <svg width="500px" height="500px">
            <rect x="0" y="0" width="100" height="100" fill="#feac5e">
                <animate attributeName="x" from="0" to="500" dur="2s" repeatCount="indefinite" />
            </rect>
        </svg>
    );
}
```