<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-11 15:39:08
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-11 16:54:40
 * @Description: 着色语言基本类型
-->

# 着色语言

[GLSL 中文手册](https://blog.csdn.net/qjh5606/article/details/82592207)

## 基本类型

| 类型 | 说明 |
| - | - |
| void | 空类型 |
| bool | 布尔类型 true 或 false |
| int | 带符号的整数 signed integer |
| float | 带符号的浮点数 floating scalar |
| vec2, vec3, vec4 | n维浮点数向量 n-component floating point vector |
| bvec2, bvec3, bvec4 | n维布尔向量 Boolean vector |
| ivec2, ivec3, ivec4 | n维整数向量 signed integer vector |
| mat2, mat3, mat4 | 2x2, 3x3, 4x4 浮点数矩阵 float matrix |
| sampler2D | 2D纹理 a 2D texture |
| samplerCube | 盒纹理 cube mapped texture |

## 常见变量类型

* `uniform`是外部程序传递给着色器（shader）的变量，在shader内部，相当于常量
* `attribute`是只在顶点着色器使用的变量，用来表示一些顶点相关的信息
* `varying`是传递顶点着色器和片段着色器的变量