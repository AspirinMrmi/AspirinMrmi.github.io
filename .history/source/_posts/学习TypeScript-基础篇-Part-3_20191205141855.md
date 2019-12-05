---
title: 学习TypeScript(基础篇)-Part.3
date: 2019-12-05 14:16:02
tags: TypeScript
categories: Love & Peace
---


![ts](https://i.loli.net/2019/12/05/h7IlaVBjeXTPQvY.jpg)

> 断更N天，肥来了肥来了。

## 任意值

任意值（any）用来表示允许赋值为任意类型

<!--more-->

### 什么是任意值类型？

当我们定义了一个普通类型的值以后，再去改变它的类型是不允许的：

```javascript
let myLuckyNumber: number = 10;
myLuckyNumber = "ten";
```

以上代码会报错，不允许将本来是number类型的变量修改为string

但是，如果我们定义了一个变量的类型为任意类型（any），它可以允许再被赋值以任何其他的类型：

```javascript
let myLuckyNumber : any = 10;
myLuckyNumber = 'ten';
```

以上代码不会报错

### 什么时候用任意值类型？

在我们编程的过程中，当我们不确定我们写的程序的变量是什么类型或者该变量类型是动态变化的时候，可以将其声明为任意值类型。

它可以使我们轻松地通过编译。

### 能否用Object取代？

不能

你可能会想用Object来替代any，但是Object只能由我们来为其指定一些值，而不能去调用它的一些方法或者属性，即使该方法或者该属性存在于这个变量之上：

```javascript
let prettySure: Object = 10;
prettySure.toFixed(); // Error: Property 'toFixed' doesn't exist on type 'Object'.
```

这里编译不会通过。

### 任意值的属性和方法

但是在任意值类型上去访问任何属性、任何方法都是可以的，都可以通过编译：

```javascript
let notSure : any = 10;
noSure.ifItExits(); // Okay, ifItExits might exits at runtime
notSure.toFixed(); // Okay, toFixed exists (but the compiler doesn't check)
```

**这里指的只是编译可以通过，在编译生成的js文件中，如果这些属性和方法不存在于这个变量上，那么也会报错**

### 未声明类型的变量

变量如果在声明之初并未指定其类型，那么它会被识别为任意值类型：

```javascript
let something;
something = 'seven';
something = 7;
something.setName('Tom');
```

上面的代码等价于：

```javascript
let something: any;
something = 'seven';
something = 7;
something.setName('Tom');
```

### 其他场景

我们不清楚一个数组里究竟是怎样的类型结构的时候

直接看代码比较直观：

```javascript
let list: any[] = [1, true, "free"];
```

