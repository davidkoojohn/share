# share
Technology sharing

****
* install jekyll
```
$ gem install jekyll
```

* 安装了 Jekyll 的 Gem 包之后，就可以在命令行中使用 Jekyll 命令了。有以下这些用法：
```
$ jekyll build
# => 当前文件夹中的内容将会生成到 ./site 文件夹中。

$ jekyll build --destination <destination>
# => 当前文件夹中的内容将会生成到目标文件夹<destination>中。

$ jekyll build --source <source> --destination <destination>
# => 指定源文件夹<source>中的内容将会生成到目标文件夹<destination>中。

$ jekyll build --watch
# => 当前文件夹中的内容将会生成到 ./site 文件夹中，
#    查看改变，并且自动再生成。
```


* dev
```
$ git clone https://github.com/davidkoojohn/share.git
$ jekyll serve
```

* Jekyll 同时也集成了一个开发用的服务器，可以让你使用浏览器在本地进行预览。
```
$ jekyll serve
# => 一个开发服务器将会运行在 http://localhost:4000/

$ jekyll serve --detach
# => 功能和`jekyll serve`命令相同，但是会脱离终端在后台运行。
#    如果你想关闭服务器，可以使用`kill -9 1234`命令，"1234" 是进程号（PID）。
#    如果你找不到进程号，那么就用`ps aux | grep jekyll`命令来查看，然后关闭服务器。[更多](http://unixhelp.ed.ac.uk/shell/jobz5.html).

$ jekyll serve --watch
# => 和`jekyll serve`相同，但是会查看变更并且自动再生成。
```

```
.
├── _config.yml   # 保存配置数据
├── _drafts       # 未发布的文章
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes     # 加载这些包含部分到你的布局或者文章中以方便重用
|   ├── footer.html
|   └── header.html
├── _layouts      # 包裹在文章外部的模板
|   ├── default.html
|   └── post.html
├── _posts        # 文章
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data         # 
|   └── members.yml
├── _site         # 一旦 Jekyll 完成转换，就会将生成的页面放在这里（默认）
└── index.html
```

```
|-- _drafts/      #　草稿
|   |-- a-draft-post.md
# pre-viws
$ jekyll serve --drafts
```



  