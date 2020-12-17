<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-16 14:04:49
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-16 14:18:36
 * @Description: git submodule
-->

# git submodule

[Git 工具 - 子模块](https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97)

git submodule update --init 和 --remote的区别
git 的submodule 工具方便第三方库的管理，比如gitlab 上的各种开源工具，spdlog等
在项目目录下创建.gitmodule 里可以添加第三方库，然后在更新第三方库时，有两个选项
git submodule update --init 这是更新当前主项目上记录的submodule 的commitid
比如在提交子项目的时候，会在主项目产生变更，这个变更随着主项目一起的提交，也就是一一对应

Subproject commit 7d67b54340cebb4ffaa283ebf6975406f8ecda0d  
Subproject commit 293633445da9133e959377bef8d61021d5cadc83
那么这个update --init 就会更新为主项目对应的版本，但是这种子项目提交的时候并不会修改.gitmodule里面的版本
这就是与remote的区别

当使用git submodule update --remote的时候，子项目会根据.gitmodule的版本进行更新

当然以上是子项目的管理，对于第三方库的管理，那一般就是直接更新.gitmodule里的版本，自己不会动别的开发的东西也不会产生提交

综上可见，如果clone 了一个含有子项目和第三方库的项目代码时，需要执行 git submodule update --remote 和 git submodule update --init 两个命令，或者调整先后，才能正确编译