---
title: '系统级 I/O'
publishDate: 2025-05-13
description: '武汉大学2025春季学期 计算机系统基础 第十章 系统级 I/O'
tags:
  - whu
  - csapp
language: '中文'
---

System-Level I/O

本章介绍 Unix I/O 和标准 I/O 的一般概念。

在某些重要情况下，不得不使用 Unix I/O 而不是高级 I/O 函数。

## Unix I/O

以 `FILE *fopen` 函数引入，其使用 C 调用了 `open`，这是系统调用，是系统级别的 I/O。很多高级 I/O 函数都是用 `open`、`read`、`write` 和 `close` 等系统调用实现的。本节就是介绍这些系统调用。

Unix I/O 是一种系统调用接口，提供了一组函数来处理对文件和设备的访问，

Unix I/O 的设计目标是简化 I/O 操作，使其尽可能简单和一致。

### Overview

- A Linux**「File」**is a sequence of m bytes.
- 所有的 I/O 设备都被视为文件，甚至内核也被视为文件。
    - `cat /proc/$$/status` 可以查看当前进程的状态。
    - 甚至每个进程都有一个 `/proc/PID` 目录，里面的 `/fd` 是该进程的文件描述符。
- 内核提供了一系列基础的文件操作：
    - `open()` and `close()` 开关文件
    - `read()` and `write()` 读写文件
    - `stat()`, `lstat()`, `fstat()` 获取文件的状态信息。
    - `lseek()` 设置下一次读写的位置，类似访问到哪个字节的指针。

### 文件类型

类型决定操作方式，包括但不限于以下内容。

**「Regular file」**

- 包括文本文件和二进制文件。
- 

**「Directory」**



**「Socket」**

