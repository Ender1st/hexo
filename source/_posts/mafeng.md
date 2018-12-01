---
title: Ender's Code Style for OI
notshow: false
comments: true
categories: OI
tags: 码风规范
abbrlink: 6569f1d0
date: 2018-08-19 22:09:13
password:
---
本文介绍博主在OI中常见代码风格，也用来规范自己。
<!--more-->
~~本文内容自发稿开始保证实施~~

# Ender's Code Style for OI

## 概览

可以使用万能头文件`#include <bits/stdc++.h>`
使用`using namespace std;`时，应放在`#include`下一行。  
结构体应放于所有函数之前，`main`函数应放于程序末尾。  

## 缩进

所有同级命令均应为等长缩放长度，所有被包含的命令应使用4个空格或等长Tab缩进。

## 大括号

对于除结构体以外的需要大括号的命令和函数，左大括号不应换行，左边必须有一个空格；右大括号与命令应为等长缩进,例：  
```
// 结构体
struct Node
{
    // do something...
}

// 其他,以if为例
if(condition) {
    // do something...
}
else {
    // do something...
}
```

除`cmp`以外的函数，右括号均应换行，`cmp`如果较短，右括号可以不换行，例：  
```
cmp(int a,int b) {return a>b;}

void search(int cur) {
    // do something...
}
```

## 行

除循环嵌套以外，如果包含的命令只有一行，应不使用大括号且不换行，例：  
`for(int i=1;i<=n;i++) cin>>a[i];`  
组合使用的代码应不换行且以空格可开，例：
`a=q.top(); q.pop()`

## 函数

`main`函数必须声明为`int main(/* sth. */)`，最后一句必须为`return 0;`,例：    
```
int main(void) {
    // do something...
    return 0;
}
```

## 变量声明

应尽量少使用全局变量。  
局部变量在需要时定义，除循环以外应尽量减少重名。  
如果一个变量更改数值非常频繁，应使用`register`注册变量，例：  
`for(register int i=1;i<=999999999;i++)`
如果一个变量确定不包含负数，且数值较大，则应使用`unsigned`无符号类型。  

## 空格

除文章其他地方规定以外，为了便于阅读检查，可在语句中适当添加空格，例：  
`int a, b, c = a + b*2;`

## 命名

数组与变量应该分行声明。  
所有函数、变量、参数名都**必须**使用“驼峰命名法”，且除辅助变量都必须有意义。  
结构体首字母应大写且名称有意义。  
例：  
```
struct Node
{
    int a, b;
}

int getRoot(int k) {
    // some commands can get root...
}
```
 ## 类型别名、常量类型变量与宏定义

较长的数应使用`const`而不是`#define`。  
较长类型名称应使用`typedef`而不是`#define`。  
当某类型代码大量使用时可以使用`#define`来缩短代码长度。

例：  
```
#define rep(i,s,n) for(int i=s;i<=n;i++)
const int maxn=1000000000;
typedef longlong ll;
ll a[maxn], b[maxn];
ll c, d;

rep(i,1,c) cin>>a[i];
```