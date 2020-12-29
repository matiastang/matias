<!--
 * @Author: tangdaoyong
 * @Date: 2020-12-28 17:43:32
 * @LastEditors: tangdaoyong
 * @LastEditTime: 2020-12-29 09:19:43
 * @Description: iTerm
-->
# iTerm

[powerline](https://github.com/powerline/fonts)
[iterm2 终端问题整理](https://blog.csdn.net/chezhan1972/article/details/100720352)
[iTerm2 + Oh My Zsh + Solarized color scheme + Meslo powerline font + [Powerlevel9k] - (macOS)（推荐](https://gist.github.com/kevin-smets/8568070)
[iTerm2 + oh my zsh + solarized + Meslo powerline font (OS X / macOS)](https://www.jianshu.com/p/0ff3269bc261)
[Mac 下终端配置（item2 + oh-my-zsh + solarized 配色方案）](http://zhuxin.tech/2017/09/21/zsh%E9%85%8D%E7%BD%AE/)
[MAC 下 iTerm 主题配置](https://www.zybuluo.com/Sweetfish/note/636550)

## 安装

### zsh自动提示与命令补全

`zsh`自动提示与命令补全比`iTerm2`自带的更强大的命令提示与补全

1. 克隆仓库到本地 `~/.oh-my-zsh/custom/plugins` 路径下
```
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
```
cd ~/.oh-my-zsh/custom/plugins
git clone git://github.com/zsh-users/zsh-autosuggestions
```
2. 用 `vim` 编辑 `.zshrc` 文件，找到插件设置命令，默认是 `plugins=(git)` ，我们把它修改为`plugins=(zsh-autosuggestions git)`
```
vim ~/.zshrc
```
3. 加载.zshrc配置
```
source ~/.zshrc
```
4. 如果重新打开终端时可能看不到变化，可能你的字体颜色太淡了，我们把其改亮一些，用 `vim` 编辑 `zsh-autosuggestions.zsh` 文件，修改`ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=10'`
```
cd ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
```

### zsh语法高亮

1. 使用`homebrew`包管理工具安装 `zsh-syntax-highlighting` 插件
```
brew install zsh-syntax-highlighting
```
2. 配置.zshrc文件，最后一行添加
```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```
3. 加载.zshrc配置
```
source ~/.zshrc
```
## 问题

### 波浪线两边的两个问号

隐藏了用户名和主机名所有看不到前面的问号。

![问题显示](./img/iTerm2显示非ascii字符问题.jpeg)

原因：

`agnoster`主题需要特殊的字体支持，因为有非ascii字符编码，这两个问号本来是为了更好看的箭头，但是箭头在当前字体中是不会被显示的。解决方法是重新下载一个支持非ascii编码的字体。

处理：
```
# 1. clone
git clone https://github.com/powerline/fonts.git
# 2.install
cd fonts
./install.sh
# 3. clean-up a bit
cd ..
rm -rf fonts
```

安装[powerline](https://github.com/powerline/fonts.git)字体，然后在`iTerm2`中应用字体 `iTerm` -> `Preferences` -> `Profiles` -> `Text` -> `font` -> `Change Font` 中选择使用 `Meslo` 字体。

![正常显示](./img/iTerm2正常显示.jpeg)

### VSCode中的命令行处理`波浪线两边的两个问号`

同样的原因，还是需要设置`VSCode`中的字体。

1. `mac`查看系统安装的字体：
```
# 进入字体目录
cd ~/Library/Fonts
# 查看字体
ls
# 部分结果
Literation Mono Powerline Bold Italic.ttf
Literation Mono Powerline Bold.ttf
Literation Mono Powerline Italic.ttf
Literation Mono Powerline.ttf
```
2. 更改`VSCode`中使用的字体

`Code` -> `Preferences` -> `Settings`搜索`font`在`Font Family`中添加需要使用的字体（需要提前安装到`mac`中，可先查看）如下添加了`Literation Mono Powerline`然后就显示正常了。
```
'Literation Mono Powerline', Menlo, Monaco, 'Courier New', monospace
```
