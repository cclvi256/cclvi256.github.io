---
title: Multithreading (I) - POSIX Process and Thread Model
date: 2024-10-10 20:00:00 +0800
categories:
  - Programming Techniques
  - Performance Optimisation
tags:
  - Linux
  - Multithreading
  - Performance Optimisation
  - Parallel Computing
  - Concurrency
  - Operating System
math: true
---

## POSIX and Linux Multitreading Model

POSIX (Portable Operating System Interface) is a family of standards specified by the IEEE Computer Society for maintaining compatibility between operating systems, which ensures the compatibility and portability between various UNIX-like systems.
Linux is mostly POSIX-compliant, indicating that Linux follows many POSIX standards.

So, naturally, Linux supports the POSIX thread model. The POSIX thread model is also supported by many programming languages.
For example, C have a header file `pthread.h` or `cpthread` for POSIX threads, and the C++ `std::thread` class of the standard library is factually the reencapsulation of the C `cpthread` library.
