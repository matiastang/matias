<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-15 17:24:28
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-15 17:32:57
 * @Description: TypeScript常见问题
-->
# TypeScript常见问题

## string类型不能作为index

> expression of type ‘string’ can’t be used to index type

当动态使用`属性`或`方法`时，会报错！
```ts
let data = {
    name: 'name'
};
let key = 'name';
let value = data[key];
console.log(value);
```
声明一个`interface`。
```ts
interface dataType {
    [key: string]: string
}
let data: dataType = {
    name: 'name'
};
let key = 'name';
let value = data[key];
console.log(value);
```