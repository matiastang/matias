<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-15 09:31:56
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-15 09:49:33
 * @Description: WebGL流程图
-->
# WebGL流程图

## 介绍

## 渲染管线流程图

![渲染管线流程图](./images/png/WebGL流程图.png)

`gl_PointSize`、`gl_Position`、`gl_FragColor`都是内置变量，也就是说不需要声明，这一点与多数编程语言不同，这主要是由GPU的特殊性决定，感兴趣的话 可以研究显卡的硬件结构，渲染管线等概念。

### 顶点着色器

`gl_Position`实际上是几何图形装配阶段的输入数据。几何图形装配过程又被称为图元装配过程，因为被装配出的基本图形（点，线，面）又被称为图元。
`gl_PointSize`

### 图元装配和光栅化

图元装配任务：

将孤立的顶点坐标装配成几何图形。几何图形的类别由`gl.drwaArrays()`函数的第一个参数决定(`WebGL七种基本图形`)。

光栅化任务：

将装配好的几何图片转化为片元。

`顶点着色器`和`片元着色器`之间的`图形装配`与`光栅化`的过程，如下图：

![图元装配和光栅化](./images/png/图元装配和光栅化.png)

### 片元着色器

`gl_FragColor`