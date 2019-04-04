---
title: Java学习笔记-1
notshow: false
comments: true
categories: Java学习笔记
tags:
  - Java
  - 笔记
abbrlink: 8b64c63b
date: 2019-02-10 11:03:07
password:
---

# Java学习笔记-1

受Minecraft Java版的影响，一直想学Java。最近终于开始着手学习，在博客里记录下来学习历程。

<!--more-->

## 安装编程环境



在官网下载安装jdk，配置环境变量，安装eclipse，汉化eclipse。



## HelloWorld

 

```java
package xin.ender.helloworld; // 包名

public class HelloWorld { // 定义公共类

	public static void main(String[] args) { // main主函数   
    	// public告知其他类可以访问这个函数
    	// static告知编译器这个函数是一个静态函数
    	// void表明main函数返回值为无类型
    	// String[] args定义一个字符串数组"args"
		System.out.print("HelloWorld");	//输出到控制台
	}

}

```

