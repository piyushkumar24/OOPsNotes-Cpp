# 📘 Chapter 10: Static Keyword in C++

---

## 🔍 Overview

The `static` keyword in C++ is a powerful feature that controls **lifetime**, **scope**, and **memory sharing** of variables and objects. This chapter dives deep into how `static` affects:
- Local variables inside functions
- Member variables inside classes
- Object lifetimes
- Memory management in OOP

Understanding `static` is crucial for writing optimized and bug-free C++ code, especially in object-oriented scenarios.

---

## 🧠 Concept Map

```
                 +--------------------+
                 |    static keyword  |
                 +--------------------+
                           |
           +---------------+---------------+
           |                               |
+-------------------+           +--------------------+
| Inside Functions  |           |  Inside Classes     |
+-------------------+           +--------------------+
| Lifetime = whole  |           | Shared by all      |
| program           |           | objects            |
| Retains value     |           | Only 1 copy exists |
| across calls      |           | Memory-efficient   |
+-------------------+           +--------------------+
                           |
              +------------+------------+
              |                         |
   +------------------+      +--------------------------+
   | Static Objects    |      | Object Scope Control     |
