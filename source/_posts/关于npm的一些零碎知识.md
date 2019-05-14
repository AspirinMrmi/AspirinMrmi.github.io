---
title: 关于npm的一些零碎知识
date: 2019-04-09 11:04:29
tags: 
      - npm
      - nrm
categories: Love & Peace
description: npm 是JavaScript 世界的包管理工具，并且是Node.js 平台的默认包管理工具。通过npm 可以安装、共享、分发代码，管理项目依赖关系。
---

## npm是什么？

npm 是JavaScript 世界的包管理工具，并且是Node.js 平台的默认包管理工具。通过npm 可以安装、共享、分发代码，管理项目依赖关系。

## npm包发布与管理

1. 首先注册一个账号，[点这里](https://npmjs.com)；
2. 在终端输入 ==npm login== 进行登录；
3. 创建一个项目文件夹，通过 ==npm init== 初始化，修改package.json里的项目信息，添加README.md.(已有项目的跳过)
4. 通过 ==npm publish== 发布(此处有坑：包名不能与现有的包重名或者非常接近)

## nrm镜像源管理

大清墙太厚，有好的vpn的话尚可，没有的话还是建议将镜像源切到国内，为了便于管理，我们引入nrm。

使用npm安装：


```
$ npm install -g nrm
```

使用yarn安装:

```
$ yarn global add nrm
```

下面我们安装一下淘宝的镜像源：

```
$ npm install cnpm -g --registry=https://registry.npm.taobao.org
```

使用 ==nrm ls== 命令查看当前所有源：


```
  npm ---- https://registry.npmjs.org/
  cnpm --- http://r.cnpmjs.org/
* taobao - https://registry.npm.taobao.org/
  nj ----- https://registry.nodejitsu.com/
  npmMirror  https://skimdb.npmjs.com/registry/
  edunpm - http://registry.enpmjs.org/
```

以上是我的所有镜像源，可以看到我当前所用的正是淘宝的镜像。如果我们想切回npm源：

```
$ nrm use npm
```
下面是一些常用的命令：

```
$ nrm ls #列出nrm管理的registry列表
$ nrm current #显示当前的registry名称
$ nrm use taobao #切换registry到taobao源，这个命令对yarn和npm同时生效
$ nrm add taobao https://registry.npm.taobao.org #添加一个名为taobao的源到列表
$ nrm del taobao #从列表中删除taobao源
```


---

参考：

http://blog.soolx.top/2019/03/31/npm-publish/

https://cnodejs.org/topic/5326e78c434e04172c006826










