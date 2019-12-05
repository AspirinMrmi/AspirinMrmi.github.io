---
title: 关于node工具的一些零碎知识
date: 2019-04-09 11:04:29
tags: 
      - npm
      - nrm
categories: Love & Peace
description: npm 是JavaScript 世界的包管理工具，并且是Node.js 平台的默认包管理工具。通过npm 可以安装、共享、分发代码，管理项目依赖关系。
---

![头](https://i.loli.net/2019/12/05/FHMsf7TEea1OAkc.jpg)

## npm是什么？

npm 是JavaScript 世界的包管理工具，并且是Node.js 平台的默认包管理工具。通过npm 可以安装、共享、分发代码，管理项目依赖关系。

<!--more-->

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
$ nrm usr npm
```
下面是一些常用的命令：

```
$ nrm ls #列出nrm管理的registry列表
$ nrm current #显示当前的registry名称
$ nrm use taobao #切换registry到taobao源，这个命令对yarn和npm同时生效
$ nrm add taobao https://registry.npm.taobao.org #添加一个名为taobao的源到列表
$ nrm del taobao #从列表中删除taobao源
```

## NVM(Mac)管理工具

在安装前建议先将本地的node模块都清空。


```
npm ls -g --depth=0  # 查看已经安装在全局的node模块

sudo rm -rf /usr/local/lib/node_modules  # 删除全局node_modules

sudo rm /usr/local/bin/node  #删除node

cd  /usr/local/bin && ls -l | grep "../lib/node_modules/" | awk '{print $9}'| xargs rm    #删除全局 node 模块注册的软链
```

安装nvm


```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
```

安装完成后重新打开终端


```
source ~/.bash_profile
```

nvm常用的命令：

- nvm install <version> ## 安装指定版本，可模糊安装，如：安装v4.4.0，既可nvm install v4.4.0，又可nvm install 4.4

- nvm uninstall <version> ## 删除已安装的指定版本，语法与install类似

- nvm use <version> ## 切换使用指定的版本node

- nvm ls ## 列出所有安装的版本

- nvm ls-remote ## 列出所有远程服务器的版本（官方node version list）

- nvm current ## 显示当前的版本

- nvm alias <name> <version> ## 给不同的版本号添加别名

- nvm unalias <name> ## 删除已定义的别名

- nvm reinstall-packages <version> ## 在当前版本node环境下，重新全局安装指定版本号的npm包

## Mac打开、编辑、保存.bash_profile

1. 根目录创建.bash_profile
```
touch .bash_profile
```
2. 编辑

```
open -e .bash_profile
```

3. 保存文件，关闭窗口
4. 更新刚刚配置的环境变量

```
source .bash_profile
```



---

参考：

http://blog.soolx.top/2019/03/31/npm-publish/

https://cnodejs.org/topic/5326e78c434e04172c006826




















