---
title: C++引用
subtitle:
date: 2025-02-08T11:57:51+08:00
slug: 1f15d8a
draft: true
description:
keywords:
license:
comment: false
weight: 0
tags:
  - C++
categories:
  - 笔记
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRelated: false
hiddenFromFeed: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: false
password:
message:
repost:
  enable: true
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---

<!--more-->
{{< figure src="picture/11.jpg"  >}}
# 左值引用与右值引用

## 1. 左值与右值

### 1.1 左值

左值是可以**取地址**的对象，比如变量名和解引用的指针变量。

```C++
// 以下的a、p、*p、b都是左值
int a = 3;
int* p = &a;
*p;
const int b = 2;
```

### 1.2 右值

右值是**不能取地址**的对象，比如常量、临时变量、函数返回值、运算符返回值等。

```C++
double x = 1.3, y = 3.8;
// 以下几个都是常见的右值
10;                 // 字面常量
x + y;             // 表达式返回值
fmin(x, y);        // 传值返回函数的返回值
```

## 2. 左值引用与右值引用

无论左值引用还是右值引用，都是给对象取别名。

### 2.1 左值引用

是指对左值的引用，作用是**避免对象拷贝**。

```C++
int& ra = a;
```

### 2.2 右值引用

是指对右值的引用，作用是**延长对象的生命周期**。

```C++
int&& rr = 10;
```

### 2.3 对比与总结

- 左值引用可以指向左值，在指向右值时需要const修饰
- 右值引用可以指向右值，在指向左值时需要std::move()

```C++
const int& rt4 = 8; // 临时对象的生命周期会被延长至引用的作用域结束
int t = 10;
int&& rrt = std::move(t);
```

## 3. 左值引用的实际意义

### 3.1 实际意义

传值传参和传值返回都会产生拷贝，而左值引用可以减少拷贝，从而提高效率。

### 3.2 短板

但当局部对象出了函数作用域以后就不存在了，所以不可以使用左值引用返回了。

## 4. 右值引用的实际意义

### 4.1 实际意义

解决函数参数的传递中（针对返回的将亡值）传递效率和空间不如意的问题。

### 4.2 短板

左值经过move()后，会失去原来的地址，所以无法再用之前的变量名访问。

### 4.3 完美转发

**函数模板**（不是类模板）中的&&不表示右值引用，而是万能引用，模板类型必须通过推断才能确定，其接收左值后会被推导为左值引用，接收右值后会被推导为右值引用。

```C++
void Func(int& x) { cout << "左值引用" << endl; }

void Func(int&& x) { cout << "右值引用" << endl; }

template<typename T>
void f(T&& t)  // 万能引用
{
    Func(t);  // 根据参数t的类型去匹配合适的重载函数
}
```

> [!NOTE]
> 右值引用后便失去了右值的属性。

f(10); 　　10是右值，传参后万能引用被推导为右值引用，但在f()函数中它变为了左值，因此实际调用的函数是void Func(int& x)。

为了实现完美转发，除了使用万能引用之外，我们还要用到std::forward（C++11），它在传参的过程中保留对象的原生类型属性。

```C++
void Func(int& x) { cout << "左值引用" << endl; }

void Func(int&& x) { cout << "右值引用" << endl; }

template<typename T>
void f(T&& t)  // 万能引用
{
    Func(std::forward<T>(t));  // 根据参数t的类型去匹配合适的重载函数
}

int main()
{

    PerfectForward(10); // 仍是右值引用

    return 0;
}
```

> [!NOTE]
> 实现完美转发需要用到万能引用和 std::forward。

---
本笔记参考了「Hoshino373」的文章，原文链接为：https://blog.csdn.net/m0_59938453/article/details/125858335