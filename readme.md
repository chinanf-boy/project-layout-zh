# golang-standards/project-layout [![translate-svg]][translate-list]

<!-- [![size-img]][size] -->

[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list

「 这是 GO 应用程序项目的基本布局 」

[中文](./readme.md) | [english](https://github.com/golang-standards/project-layout)

---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'golang-standards/project-layout' -->
<!-- commit = 'a98d2d4e92a85f96cc43d2d59b466882afe841b1' -->
<!-- time = '2018-10-05' -->
翻译的原文 | 与日期 | 最新更新 | 更多
---|---|---|---
[commit] | ⏰ 2018-10-05 | ![last] | [中文翻译][translate-list]

[last]: https://img.shields.io/github/last-commit/golang-standards/project-layout.svg
[commit]: https://github.com/golang-standards/project-layout/tree/a98d2d4e92a85f96cc43d2d59b466882afe841b1

<!-- doc-templite END generated -->

### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[If help, **buy** me coffee —— 营养跟不上了，给我来瓶营养快线吧! 💰](https://github.com/chinanf-boy/live-need-money)

---

### 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [标准 Go 项目布局](#%E6%A0%87%E5%87%86-go-%E9%A1%B9%E7%9B%AE%E5%B8%83%E5%B1%80)
  - [Go 目录](#go-%E7%9B%AE%E5%BD%95)
    - [`/cmd`](#cmd)
    - [`/internal`](#internal)
    - [`/pkg`](#pkg)
    - [`/vendor`](#vendor)
  - [服务应用目录](#%E6%9C%8D%E5%8A%A1%E5%BA%94%E7%94%A8%E7%9B%AE%E5%BD%95)
    - [`/api`](#api)
  - [Web 应用程序目录](#web-%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%9B%AE%E5%BD%95)
    - [`/web`](#web)
  - [通用应用程序目录](#%E9%80%9A%E7%94%A8%E5%BA%94%E7%94%A8%E7%A8%8B%E5%BA%8F%E7%9B%AE%E5%BD%95)
    - [`/configs`](#configs)
    - [`/init`](#init)
    - [`/scripts`](#scripts)
    - [`/build`](#build)
    - [`/deployments`](#deployments)
    - [`/test`](#test)
  - [其他目录](#%E5%85%B6%E4%BB%96%E7%9B%AE%E5%BD%95)
    - [`/docs`](#docs)
    - [`/tools`](#tools)
    - [`/examples`](#examples)
    - [`/third_party`](#third_party)
    - [`/githooks`](#githooks)
    - [`/assets`](#assets)
    - [`/website`](#website)
  - [你不应该拥有的目录](#%E4%BD%A0%E4%B8%8D%E5%BA%94%E8%AF%A5%E6%8B%A5%E6%9C%89%E7%9A%84%E7%9B%AE%E5%BD%95)
    - [`/src`](#src)
  - [徽章-Badges](#%E5%BE%BD%E7%AB%A0-badges)
  - [记](#%E8%AE%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 标准 Go 项目布局

这是 GO 应用程序项目的基本布局。它不是由核心 Go dev 团队定义的官方标准;但是,它是 Go 生态系统中一组集合历史上常见以及正在使用的项目布局模式。其中一些模式比其他模式更受欢迎。它还有一些小的增强,以及一些对于任何一个大真实世界应用程序，都通用的支持目录。

如果你正在努力学习 GO,或者如果你正在为自己建一个 PoC 或一个玩具项目, 那这个项目布局就对你来说是一个**过激**的项目。从简单`main.go`文件开始(一个简单的事情)是绰绰有余的。随着项目的发展,请记住,确保代码结构良好是非常重要，否则最终将导致具有许多隐藏的依赖项和全局状态的混乱代码。当更多的人在这个项目上工作时，你需要更多的结构。这个时候，引入一种管理包/库的常用方法，成为了必要。当您有一个开源项目，或者当您知道其他项目从您的项目存储库导入代码时，就需要私有(又名`内部`)包和代码。**现在**，Clone 此`project-layout`库，保存你需要的东西，删除所有其他东西! 不要因为它在那里，就表示你必须使用它。这些模式并不是在每一个项目中使用。即使是`vendor`模式也不是普遍的。

这个项目布局是通用为主的，它不试图强加一个特定的 GO 封装结构.

这是社区的努力。打开一个**Issue**,如果你看到一个新的模式,或者如果你认为一个现有的模式需要更新.

如果你需要帮助命名,格式化和风格开始运行, 请[`gofmt`](https://golang.org/cmd/gofmt/)和[`golint`](https://github.com/golang/lint). 同时请务必阅读这些 GO 代码风格指南和建议:

- https://talks.golang.org/2014/names.slide
- https://golang.org/doc/effective_go.html#names
- https://blog.golang.org/package-names
- https://github.com/golang/go/wiki/CodeReviewComments

可查看[`Go Project Layout`](https://medium.com/golang-learn/go-project-layout-e5213cdcfaa2)的历史背景信息.

更多关于包的命名和组织的工作建议: 其他代码结构

- [GopherCon EU 2018: Peter Bourgon - Best Practices for Industrial Programming](https://www.youtube.com/watch?v=PTE4VJIdHPg)
- [GopherCon Russia 2018: Ashley McNamara + Brian Ketelsen - Go best practices.](https://www.youtube.com/watch?v=MzTcsI6tn-0)
- [GopherCon 2017: Edward Muller - Go Anti-Patterns](https://www.youtube.com/watch?v=ltqV6pDKZD8)
- [GopherCon 2018: Kat Zien - How Do You Structure Your Go Apps](https://www.youtube.com/watch?v=oL6JBUk6tj0)

## Go 目录

### `/cmd`

本项目的主要应用.

目录名称，应匹配的每个应用程序可执行文件的名字(例如,如果你有你想要的`/cmd/myapp`).

不要在此目录中放置大量代码。如果您认为代码可以导入，并在其他项目中使用,那么它应该存在于`/pkg`目录。如果代码不可重用,或者如果不希望其他人重用它,请将代码放入`/internal`目录。你永远不知道别人会做什么,所以明确你的意图!

有一个简单，常见的`main`函数，它从`/internal`和`/pkg`目录导入和调用代码，然再也没有什么了.

见[`/cmd`](cmd/README.md)目录的例子.

### `/internal`

私有应用程序和库代码。这是你不希望别人在他们的应用程序或库中导入的代码.

将实际应用程序代码放入`/internal/app`目录(例如,`/internal/app/myapp`和这些应用程序共享的代码`/internal/pkg`目录(例如,`/internal/pkg/myprivlib`)

### `/pkg`

由外部应用程序使用的库代码(例如,`/pkg/mypubliclib`)。其他项目将导入这些库,并希望它们能工作,所以在你把东西放在这里之前要三思:

当根目录包含许多非 Go 组件和目录时,它还可以将 Go 代码分组到一个地方,从而更容易运行各种 Go 工具(如[`Best Practices for Industrial Programming`](https://www.youtube.com/watch?v=PTE4VJIdHPg)来自 GopHeCon EU 2018).

查看[`/pkg`](pkg/README.md)，如果您想知道哪些流行的 Go repos 使用此项目布局模式。这是一种常见的布局模式,但它不被普遍接受,而 GO 社区中的一些人并不推荐它.

### `/vendor`

应用程序依赖(手动管理，或您喜欢的依赖管理工具)[`dep`](https://github.com/golang/dep))

如果你正在构建一个库,不要提交你的应用程序依赖项.

## 服务应用目录

### `/api`

OpenAPI/Swagger 规范,JSON **schema-模式**文件,协议定义文件.

见[`/api`](api/README.md)目录的例子.

## Web 应用程序目录

### `/web`

Web 应用程序特定组件:静态 Web 资产、服务器端模板和 SPAs.

## 通用应用程序目录

### `/configs`

配置文件模板,或默认配置文件.

把你的`confd`或`consul-template`模板文件在这里.

### `/init`

系统初始化(systemd, upstart, sysv)和进程管理器/监控器(runit, supervisord)配置.

### `/scripts`

执行各种构建、安装、分析等操作的脚本.

这些脚本，可让根目录的 Makefile 文件，保持小而简单(例如,`https://github.com/hashicorp/terraform/blob/master/Makefile`)

见[`/scripts`](scripts/README.md)目录的例子.

### `/build`

打包装与持续集成.

将云(AMI)、容器(Docker)、OS(deb、rpm、pkg)包配置和脚本放入`/build/package`目录.

把你的 CI(travis, circle, drone)配置和脚本放在`/build/ci`目录。请注意,一些 CI 工具(例如,Travis CI)对配置文件的位置非常挑剔。在尝试将配置文件放入`/build/ci`之后，请将它们链接到 CI 工具期望的位置(如果可能的话).

### `/deployments`

IaaS、PaaS、system 和 _容器编排部署_ 配置和模板(docker-compose, kubernetes/helm, mesos, terraform, bosh).

### `/test`

额外的外部测试应用程序和测试数据。发挥你的想象，随意构造`/test`。或对于更大的项目来说,有一个数据子目录是有意义的。例如,你可以拥有`/test/data`或`/test/testdata`，如果你需要去忽略那个目录中的内容。注意,Go 还将忽略以`.` or `_`开头的目录或文件,因此在如何命名测试数据目录方面，具有更大的灵活性.

见[`/test`](test/README.md)目录的例子.

## 其他目录

### `/docs`

设计理念和用户文档(除 godoc 生成的文档之外).

见[`/docs`](docs/README.md)目录的例子.

### `/tools`

支撑该项目的工具。请注意,这些工具可以从`/pkg`和`/internal`目录导入和使用代码.

见[`/tools`](tools/README.md)目录的例子.

### `/examples`

您的应用程序和/或公共包的示例.

见[`/examples`](examples/README.md)目录的例子.

### `/third_party`

外部辅助工具、被 fork 的代码和其他第三方实用程序(例如,Swagger UI).

### `/githooks`

Git 钩子.

### `/assets`

与你存储库一起使用的其他资产(图像、logos 等).

### `/website`

如果您不使用 Github pages，这是放置项目网站的地方.

见[`/website`](website/README.md)目录的例子.

## 你不应该拥有的目录

### `/src`

一些 GO 项目确实有`src`文件夹,但它通常发生在 Java 世界的开发，它是一种常见的模式。如果你能让自己不要尝试采用这种 Java 模式。你真的不想让你的 GO 代码或 GO 项目看起来像 Java:

不要混淆项目级别的`/src`目录与 GO 使用的其`/src`目录工作空间,如[`How to Write Go Code`](https://golang.org/doc/code.html). 这个`$GOPATH`环境变量在非 Windows 系统上，指向您的(当前)工作区(默认情况下)，指向`$HOME/go`。这个工作区包括顶层`/pkg`,`/bin`和`/src`目录.您的实际项目最终只是`/src`的一个子目录下，所以如果你项目中有`/src`目录项目，那路径将是这样的:`/some/path/to/workspace/src/your_project/src/your_code.go`. 注意,使用 GO 1.11 可以让你项目在`GOPATH`外部可用，但这并不意味着使用这个布局模式是个好主意.

## 徽章-Badges

- [Go 成绩单](https://goreportcard.com/)它会用`gofmt`,`go vet`,`gocyclo`,`golint`,`ineffassign`,`license`和`misspell`扫描你代码。 替换`github.com/golang-standards/project-layout`与您的项目参考.

- [GoDoc](http://godoc.org)提供 GoDoc 生成文档的在线版本。请将链接更改为指向你项目的链接.

- **发布-Release**-它将显示项目的最新发布号.更改 Github 链接指向您的项目.

[![Go Report Card](https://goreportcard.com/badge/github.com/golang-standards/project-layout?style=flat-square)](https://goreportcard.com/report/github.com/golang-standards/project-layout)
[![Go Doc](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat-square)](http://godoc.org/github.com/golang-standards/project-layout)
[![Release](https://img.shields.io/github/release/golang-standards/project-layout.svg?style=flat-square)](https://github.com/golang-standards/project-layout/releases/latest)

## 记

一个更具自信心的项目模板,具有可重用的配置、脚本和代码。一个**WIP-工作正在进行中**.
