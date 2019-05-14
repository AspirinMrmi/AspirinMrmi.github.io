---
title: 学习TypeScript(基础篇)-Part.2
date: 2019-04-10 21:57:21
tags: TypeScript
categories: Love & Peace
---

> ### 把自己不喜欢的事情做好看

## 原始数据类型

接下来主要学习Ts的基本概念和常用类型。

Js的类型分为：

- 原始数据类型
- 对象类型

原始数据类型包括：

- undefined
- null
- bool
- number
- string
- Symbol(Es6新增)

下面一次介绍这几种基本类型在ts中的应用

### 空值

在js中是没有空值的概念的，但是在ts中，可以使用void表示没有任何返回值的函数：


```
function alertName(): void {
    alert('My name is Tom');
}
```

声明一个void类型并没有什么卵用，因为你只能将它赋值为undefined和null。


```
let unusable: void = undefined
```

### null 和 undefined

在ts中，可以使用null和undefined来定义这两个原始数据类型：


```
let u: undefined = undefined;
let n: null = null;
```

undefined的类型的变量只能被赋值为undefined，null类型的变量只能被赋值为null。

与void的区别是：

undefined和null是所有类型的子类型：

```
let num: number = undefined;
```

or like this:

```
let u: undefined;
let num: number = u;
```

而`void`类型的变量不能赋值给`number`类型的变量

```
let v: void;
let num: number = v;
```

如上会报错：

![image](https://ws4.sinaimg.cn/large/006tNc79ly1g1xv1bb3odj30ta06kt9e.jpg)

### bool

布尔值比较简单了就：

```
let isBeautiful: boolean = true;
```

### number

`number`类型也比较简单：

```
let luckyNumber: number = 666;
```

这里`666`可以是其他进制数字。

### string

我觉得理解起来很容易，直接上代码：

```
let myName: string = Aspirin;
let myAge: number = 26;
let compose: string = `My name's ${myName},I'm ${myAge} years old`
```

上面我们引入了Es6的模板字符串。

OK，我们通过对原始数据类型在ts中是如何定义运用，也顺道复习了一下js中的基本数据类型都有啥子，面试经常问，虽然很基础，但还是希望自己不要栽跟头。

以上，Good night。


### FAQ

- 我们在讨论null和undefined的时候，正常情况下是会报错的：
![image](https://ws2.sinaimg.cn/large/006tNc79ly1g1xv32gpyxj30ts072js4.jpg)这里我们需要把tsconfig文件里的strictNullChecks关闭掉。
- 如Part1所说的，我可以通过`tsc`命令来编译我们写的ts文件，然后可以通过`node`命令去看看结果是不是我们所期望中的，算是个tips吧。





