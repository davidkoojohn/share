# Yeoman

要启动一个项目，最先要做什么？当然是搭建一个目录结构，新建一个带项目名字的文件夹，再新建一个app文件夹，里面要有common，css，img ... 对了，还要有test文件夹写单元测试，嗯 ~ 大概长这样子吧


#### File Structure
```
ProjectName/
├── app/
│    ├── src/
│    │    ├── common/
│    │    │    ├── app.js
│    │    │    ├── directives.js
│    │    │    ├── filters.js
│    │    │    ├── services.js
│    │    │    └── controllers.js
│    │    ├── css/
│    │    ├── img/
│    │    ├── js/
│    │    ├── lib/
│    │    └── module/
│    │          ├── header/
│    │          └── footer/
│    │                ├── js/
│    │                └── view/
│    ├── dist/
│    │    ├── css/
│    │    ├── js/
│    │    └── html/
│    └── index.html
│                 
├── test/
│    ├── unit/
│    ├── e2e/
│    └── karma.conf.js
│
├── node_modules/
│
└── package.json
```

**等等！NO！NO！ 我们说好的自动化呢？这样子太low了！**

怎么确定自己的目录结构是合理高效的呢？在团队协作中，（幻想一下）身为架构师的你怎么保证团队立项是合乎规范的呢？那些配置文件呢，也要一个个建立吗？为了解决这么low的行为，这时候 YEOMAN 出现了！

![yeoman](../../assets/images/yeoman/yo.png)

## [Yeoman](http://yeoman.io/)

> The web's scaffolding tool for modern webapps!

## 为什么有Yeoman

这里就得提一下前端自动化工具，前端集成解决方案

#### 什么是前端集成解决方案？
> * 草根派：解决前端工程的根本问题
> * 学院派：一套包含框架和工具（实现目的和基础），便于开发者快速构建美丽实用（要达到的目的）的web应用程序的工作流，同时这套工作流必须是稳健强壮的

解决哪些前端问题：
1. 开发团队代码风格不统一，	如何强制开发规范
2. 前期开发的组件库如何维护和使用
3. 如何模块化前端项目
4. 服务器部署前必须压缩，检查流如何简化，流程如何完善
5. ...

自动化工具:
* yeoman
* Codekit	
* FIS (baidu)
* spirit (alloyteam)
* ...

> 在web项目立项阶段，使用yeoman来生成项目的文件，代码结构自动	将最佳实践，和工具整合进来，大大加速和方便了我们后续的开发

## 安装，使用Yeoman
```
$ npm install -g yo
```

## Generator又是什么? 为什么要有他?怎么使用?

Yeoman by itself doesn't make any decisions. Every decision is made by generators which are basically plugins in the Yeoman environment.

```
$ npm install -g yo
$ npm install -g generator-webapp
$ yo webapp
```

## Yeoman用到的tool?

![yeoman](../../assets/images/yeoman/yeoman.jpg)

* the scaffolding tool (yo)
* the build tool (Gulp, Grunt etc)
* the package manager (like npm and Bower).











