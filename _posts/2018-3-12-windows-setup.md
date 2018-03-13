---
title: windows 开发环境配置
date: 2018-3-12
categories: [developer]
tags: [dev]
excerpt_separator: <!--more-->
---

### 让人头大的 windows 环境下做开发时的环境配置咋歘嘞？

> `PS:` 本人很不愿意在 win 环境下做开发，是真的不想.

<!--more-->

## 不干其他的先安装 git

> 因为操作不了 bash shell, 这是最操蛋的地方，所以我第一部先安装

1. 去 [Git](https://git-scm.com/downloads) 官网下载，这就不用多说了，作为开发者不会连一个 Gui 的安装过程操作不了
2. 配置 Git, 名字 & Email 必配，来配置个全局的的

```
$ git config --global user.name 'davidkoojohn'
$ git config --global user.email 'davidkoojohn@gmail.com'
...

// 查看 git 配置信息
$ git config --list
```

3. git 安装好之后那就必然轮到配置 ssh 了

```
// 第一步创建 `.ssh` 文件夹
$ mkdir ~/.ssh

// 第二步用 `your email` 生成 `ssh key`
$ ssh-keygen -t rsa -C "davidkoojohn@gmail.com"
// 一路 `enter` 然后键生成 id_rsa & id_rsa.pub

// 然后就添加公钥到 github 或者其他平台
$ cat ~/.ssh/id_rsa.pub
// 复制粘贴即 Ojbk

// 然后尝试连接 github
$ ssh git@github.com
// 提示 succeed 即 ssh 配置ok
```

4. 未完待续

> 敬请期待
