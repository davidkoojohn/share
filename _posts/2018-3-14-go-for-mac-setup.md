---
title: Mac 配置 Go 开发环境
date: 2018-6-20
categories: [developer]
tags: [dev]
excerpt_separator: <!--more-->
---

### Go (also known as Golang) is an open source programming language maintained by Google.

<!--more-->

# Installation

```
$ brew install golang
```

When installed, try to run `go version` to see the installed version of Go.

# Setup your workspace

## Add environment variables

Go has a unique approach of managing code where you have a single workspace for all your Go projects.

First, you'll need to tell Go the location of your workspace. We'll do this by adding some environment variables in your shell config file (usually `.bash_profile`, `.bashrc` or `.zshrc`).

```
export GOPATH=$HOME/go
export GOROOT=/usr/local/opt/go/libexec
export GOBIN=$GOPATH/bin
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
```

使修改立刻生效，run: 

```
$ source .zshrc
```

查看下 go 的环境变量

```
$ go env
```

## Create your workspace

Create the workspace directories tree:

```
$ mkdir -p $GOPATH $GOPATH/src $GOPATH/pkg $GOPATH/bin
```

`$GOPATH/src` This is where your Go projects are located `$GOPATH/pkg` A folder that contains every package objects `$GOPATH/bin` The compiled binaries home

# Write your first program

Create a file in your `$GOPATH/src`, for example `hello.go`, and input the following code

```
package main
import "fmt"

func main() {
    fmt.Printf("hello, world\n")
}
```

Run the program by running:

```
$ go run hello.go
```

If you wish to compile it and move it to `$GOPATH/bin`, then run:

```
$ go install hello.go
```

Since we have `$GOPATH/bin` added to our $PATH, you can run your program from anywhere:

```
$ hello
```

# ...

