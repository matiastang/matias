<!--
 * @Author: tangdaoyong
 * @Date: 2021-01-12 16:20:10
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2021-01-12 16:21:42
 * @Description: UIActivityViewController分享PDF文件到微信
-->
# UIActivityViewController分享PDF文件到微信

采用UIActivityViewController分享PDF文件到微信:

1. 仅仅将PDF文件的本地文件系统URL传递给UIActivityViewController 时，分享选项会包含微信、QQ、拷贝到微信、拷贝到QQ；
2. 仅仅将PDF二进制数据传递给UIActivityViewController 时，不会看到微信、QQ相关的分享途径选项；
3. 将本地文件系统URL和二进制数据都传递给*UIActivityViewController *时，分享选项会包含 拷贝到微信、拷贝到QQ ，不包含 微信、QQ ；


利用UIActivityViewController 分享PDF文件到微信的正确操作步骤如下：

1.读取该PDF文件的二进制数据；
```swift
let data = NSData.init(contentsOf: newFileURL)
```
2.获取该PDF文件的本地文件系统路径；
```swift
let fileURL = URL.init(fileURLWithPath: filePath)
```
3.将路径和数据都传递给
```swift
UIActivityViewController.init(activityItems: [data, fileURL], applicationActivities: nil)
```