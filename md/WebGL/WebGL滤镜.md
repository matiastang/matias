<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-11 15:53:00
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-11 17:13:12
 * @Description: WebGL滤镜
-->

# WebGL滤镜

[滤镜实践](https://juejin.cn/post/6883725230385299469)
[3D LUT 滤镜颜色映射原理剖析与JS实现](https://www.zhangxinxu.com/wordpress/2020/02/3d-lut-principle/)
[用3D LUT滤镜我做了个在线专业电影级别照片调色工具](https://www.zhangxinxu.com/wordpress/2017/12/3d-lut-filter-web-photoshop-film/)
[滤镜算法](https://github.com/BradLarson/GPUImage/blob/master/framework/Source/GPUImageiOSBlurFilter.m)

## 灰度

```
我们可以通过下面几种方法，将其转换为灰度：
1.浮点算法：Gray=R*0.3+G*0.59+B*0.11
2.整数方法：Gray=(R*30+G*59+B*11)/100
3.移位方法：Gray =(R*76+G*151+B*28)>>8;
4.平均值法：Gray=（R+G+B）/3;
5.仅取绿色：Gray=G；
通过上述任一种方法求得Gray后，将原来的RGB(R,G,B)中的R,G,B统一用Gray替换，形成新的颜色RGB(Gray,Gray,Gray)，用它替换原来的RGB(R,G,B)就是灰度图了。
```