---
layout:     post
title:      "前端开发mac装机指南"
date:       2019-09-23 12:00:00
author:     "Hxz"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 技术
---

# 前端开发mac装机指南

## 环境准备

首先打开app store 安装Xcode，并打开，安装components。很多东西会在Xcode里面自带，例如git。

## 环境基本配置

安装brew，打开brew官方网站，复制安装代码，在终端中粘贴并安装。

运行 ```brew install caskroom/cask/brew-cask```

运行 ```brew tap caskroom/versions```

## Shell转变

运行 ```brew install zsh```

安装完成后，运行```sudo vi /etc/shells```，在文件的末尾加上一行 ```/usr/local/bin/zsh```

保存后，运行```chsh -s /usr/local/bin/zsh```，可能需要输入密码
运行```sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"```，开始安装oh-my-zsh，安装完成后显示AsciiArt，即表示安装完成
运行 ```brew cask install iterm2``` ，安装iterm2，之后都使用iterm2

## 前端开发环境

首先安装node.js，这里直接使用nvm作为node.js的管理工具。
所以先安装nvm，运行 ```curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash```
安装成功后重新打开终端，输入nvm查看是否安装成功
然后输入 ```nvm install stable```  安装最新稳定版 node
然后安装一些常用的工具，例如：
yarn: ```npm i -g yarn```
webpack: ```npm i -g webpack```

## vscode安装

访问vscode官网直接下载vscode最新版本。

### 一些推荐的vscode插件

#### 外观

主题：Brackets Light Pro ，浅色系主题，个人比较喜欢
图标：VSCode Great Icons，给不同类型的文件配置不同的图标，非常直观；
字体：Fira Code，自从发现并开始使用 Fira Code，我就再也没多看自其它字体一眼，字体如果比较优雅，尤其是对数学运算符的处理，写代码时你真的会感觉在写诗，哈哈，Fira Code 的安装过程稍微复杂点，但是效果绝对是值当的；

#### 风格检查

ESLint：插件式架构，有多种主流的编码风格规则集可供选择，典型的有 Airbnb、Google 等，你甚至可以攒个自己的，按下不表；
StyleLint，同样插件式架构的样式检查工具，不过我在配置其检查 react-native 中 styled-components 组件样式时确实费了不小的功夫，可以单独写篇文章了；
TSLint：TypeScript 目前不是我的主要编程语言，但也早早的准备好了；
MarkdownLint：Markdown 如果不合法，可能在某些场合导致解析器异常，因为 Markdown 有好几套标准，在不同标准间部分语法支持可能是不兼容的；

#### 其他
gitLens: 可以查看git的修改记录，快速查看代码上次是谁修改的，非常方便

## 其他软件推荐

Go2Sheel，可以在Finder里加一个图标，点击即在此目录打开终端
Sketch，前端必备，和交互设计师合作很方便
SourceTree或Tower，很优秀的git可视化工具，用命令的可以无视
MacDown，一款免费markdown编辑器，Mou也很好，只是在当前版本下很卡
Charles，抓包工具，我只是觉得chrome developer tool就很好用了
Offie 2016，不得不说微软的这个产品还是挺棒的
