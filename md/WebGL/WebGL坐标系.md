<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-10 17:46:49
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-10 17:57:29
 * @Description: WebGL坐标系
-->
# WebGL坐标系

`WebGL`顶点坐标系是以中心点为原点(0, 0)的直角坐标系，`Y`轴由下到上，`X`轴由左到右。

`WebGL`纹理坐标系是以左下角原点(0, 0)的直角坐标系，`Y`轴由下到上，`X`轴由左到右。

`WebGL`纹理坐标系统中的`t`轴（你也可以直接理解为`Y`轴）方向和`PNG`，`BMP`，`JPG`等格式的图片的坐标系统的`Y`轴方向是相反的(图片原点在左上角，`Y`轴由上到下)。因此需要将图片的`Y`轴进行反转，才能够正确的将图片映射到图形上（也可以在着色器中手动反转`t`坐标）。

我们可以调用`WebGL`提供的`API`来实现。
```js
gl.pixelStorei(gl.UNPACK_FLIP_Y_WEBGL, 1);
```