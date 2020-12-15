<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-15 09:53:56
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-15 09:53:56
 * @Description: WebGL API
-->
# WebGL API

## 介绍

WebGL API指的就是gl=canvas.getContext('webgl')返回对象gl的一系列绘制渲染方法，通过WebGL API可以把一个三维场景绘制渲染出来。

WebGL API多数与GPU硬件相关，控制相关图形处理单元，比如说通过gl.createShader()、gl.shaderSource()等方法可以对着色器代码进行编译，然后在GPU的着色器单元上执行；比如说drawArrays不执行，GPU渲染管线的顶点、片元着色器是不会把顶点坐标转化为显示器上的像素显示出来。

如果你有 数字电路的知识，可编程芯片不仅仅只有GPU，针对不同的应用情形，都有特定的可编程芯片，图形处理用到的是可编程GPU，也就是说可以运行程序。处理声音是声卡，处理图像是显卡，自然而然它们 都会以CPU为核心，接受CPU的调度。以上描述在有些地方可能不太严谨，大家也不必记忆，主要目的是让大家有基本的认识，可以更好的编写程序。GPU相比CPU最大的特点是并行计算，不过WebGL API都 进行了封装，如果你想学习并行计算可以关注CUDA或OpenCL。GPU硬件(渲染管线)、显卡驱动、操作系统、浏览器、WebGL API是逐层抽象的。每一层都会为上一层提供一个接口，这里可以看出WebGL API是 首先通过浏览器的的解析，才能够经过一系列层驱动GPU工作，生成像素缓存，显示器会按照一定的频率扫描像素缓存，最终显示出来。

## API

### createShader

### shaderSource

### drawArrays