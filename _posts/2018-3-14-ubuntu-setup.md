---
title: Ubuntu 开发环境配置（前端篇）
date: 2018-3-14
categories: [developer]
tags: [dev]
excerpt_separator: <!--more-->
---

### 本指南介绍了在新Ubuntu上设置前端开发环境的基础知识。无论您是否是经验丰富的前端程序员，本文都适合参考。

<!--more-->

## chrome

    1. Google 搜索提供 Chrome 的下载源, 然后将下载源加入到系统的源列表。

    > 本人推荐也是一直使用的一个源, 如下:

    ```
    $ sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
    ```

    2. 导入谷歌软件的公钥，用于下面步骤中对下载软件进行验证。如果顺利的话，命令将返回“OK”。

    ```
    $ wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
    ```

    3. 对当前系统的可用更新列表进行更新。

    ```
    $ sudo apt-get update
    ```

    4. 执行对谷歌 Chrome 浏览器（稳定版）的安装。

    ```
    $ sudo apt-get install google-chrome-stable
    ```

    5. 锁定到启动器

    ```
    $ /usr/bin/google-chrome-stable
    ```

## git

    1. 安装 git

    ```
    $ sudo apt-get install git
    // 如果失败用一下方法安装

    $ sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext \ libz-dev libssl-dev
    // Git 的工作需要调用 curl，zlib，openssl，expat，libiconv 等库的代码，所以需要先安装这些依赖工具。
    ```

    2. 配置

    ```
    $ git config --global user.name 'your name'
    $ git config --global user.email 'your-mail@xxx.com'
    ```

## ssh

```
$ cd ~/

// 然后执行
$ ssh-keygen -t rsa -C 'your-mail@xxx.com'

// 然后检查 ~/.ssh 目录下的 文件
// 添加 id_rsa.pub (即公钥到 github)
// 尝试链接 github
$ ssh git@github.com

// 返回 succeed 即配置 ok
```

## zsh

```
// 安装 zsh
$ sudo apt-get install zsh

// 切换 bash -> zsh 设置 zsh 为默认 shell
$ sudo chsh -s $(which zsh)

// 注销重新登录
```

## oh my zsh

[主题配置](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)自己选择，只需修改 `~/.zshrc` 文件 ZSH_THEME 的值 ok

> 推荐一 zsh 的神器插件 [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)
* **[How to install](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md)**

## [nvm](https://github.com/creationix/nvm)

> 为什么要安装 [nvm](https://github.com/creationix/nvm) 呢？ 因为用 nvm 管理 node 多版本强大，和用 rvm 管理 ruby 类似

```
$ wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

## Node.js

> 已经安装了 nvm 了所以安装 node 就更加方便了

```
// 使用 nvm 安装 node
$ nvm install node

// nvm 具体使用方法使用 `nvm --help` 查看
$ nvm --help
```

## [nrm](https://github.com/Pana/nrm)

> 国内使用 npm 源太慢，大部分人会直接更改为国内的 cnpm 源或者其他 的源但是会影响 node 包的发布又得切换回去很不方便，使用 nrm 来管理就容易的多了

```
$ npm install -g nrm

// 查看 node 全局的包
$ npm ls -g --depth 0

// 查看可以使用的 npm 源
$ nrm ls

// switch registry to cnpm
$ nrm use cnpm

// nrm 具体使用方法使用 `nrm --help` 查看
```

## [yarn](https://yarnpkg.com/en/)

> 本人非常喜欢用 yarn 来做 node 包管理器

```
$ npm install -g yarn
```

## [JetBrains IDEs](http://www.jetbrains.com/)

> 本人用过无数的 ides 但是最终回归 jetbrains 家的， 在写 ruby 时才知使用 rubymine 有多好，前端推荐 [WebStorm](http://www.jetbrains.com/webstorm/)

激活 jetbrains ides 的 license server， Google 一大堆，自己搞定，这都不是事

## weapp

> 前端避免不了写小程序，可是官方的 ide 用来写代码实在太烂，只适合调试预览，还没有适配 ubuntu 的，不过 github 上有开源项目[wechat_web_devtools](https://github.com/cytle/wechat_web_devtools), readme 写的很清晰自己看着一步一步装

推荐使用 **WebStorm** 来写代码具体配置如下：

    1. 首先FileType下Cascading Style Sheet 添加*.wxss， FileType下HTML 添加*.wxml
    2. 将其中的[wecharCode.jar](https://github.com/miaozhang9/wecharCodejar)下载下来，然后在webStorm 的 File -> import settings 中导入即可

    > 如果使用的 wepy 开发

    3. 安装Vue plugin；然后FileType下Vue 添加 *.wpy

## 未完待续。。。
