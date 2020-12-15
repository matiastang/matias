<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-14 14:46:08
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-14 15:19:16
 * @Description: file content
-->
# GLSL着色器的正确文件扩展名

[GLSL着色器的正确文件扩展名是什么？](https://qa.1r1g.com/sf/ask/450298691/)
[glslang](https://www.khronos.org/opengles/sdk/tools/Reference-Compiler/)


规范中没有官方扩展名.OpenGL不处理文件中的加载着色器; 您只需将着色器代码作为字符串传递,因此没有特定的文件格式.

但是glslang,Khronos的参考GLSL编译器/验证器,使用以下扩展来确定该文件的着色器类型:

* .vert - 顶点着色器
* .tesc - 曲面细分控制着色器
* .tese - 曲面细分评估着色器
* .geom - 几何着色器
* .frag - 片段着色器
* .comp - 计算着色器

> vscode 安装扩展 `WebGL GLSL Editor`实现高亮提示。