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
   +------------------+      +--------------------------+
   | Lifetime =        |      | Object destroyed only    |
   | till end of main  |      | at end of program        |
   +------------------+      +--------------------------+
```

---

## 🧱 Detailed Sections

### 1️⃣ Static Variables Inside Functions

- Created only **once** during the entire program's execution.
- Retains its value between function calls.
- Useful for tracking state across calls.

#### 🔹 Example

```cpp
void fun() {
    static int x = 0;
    cout << "x = " << x << endl;
    x++;
}
```

Each time `fun()` is called, `x` will continue increasing.

---

### 2️⃣ Static Variables in Classes

- Declared using the `static` keyword inside the class.
- **Shared across all objects** of that class.
- Not tied to any specific object instance.

#### 🔹 Example

```cpp
class A {
public:
    static int x;

    void increment() {
        x++;
    }
};

int A::x = 0;
```

Here, `x` is shared across all instances of class `A`.

---

### 3️⃣ Static Objects and Their Lifetime

- A `static` object is created **only once**.
- Its lifetime extends until the program ends.
- Even if declared inside a block, its destructor is called at program termination.

#### 🔹 Example

```cpp
class ABC {
public:
    ABC() {
        cout << "Constructor called\n";
    }
    ~ABC() {
        cout << "Destructor called\n";
    }
};

int main() {
    if (true) {
        static ABC obj;
    }
    cout << "End of main\n";
    return 0;
}
```

**Output:**
```
Constructor called
End of main
Destructor called
```

---

## 🧪 Practical Examples

### 🔸 Without Static (Function Variable)

```cpp
void fun() {
    int x = 0;
    cout << x << endl;
    x++;
}
```

**Output:**
```
0
0
0
```

### 🔸 With Static (Function Variable)

```cpp
void fun() {
    static int x = 0;
    cout << x << endl;
    x++;
}
```

**Output:**
```
0
1
2
```

---

### 🔸 Without Static (Class Members)

```cpp
class A {
public:
    int x = 0;
    void increment() {
        x++;
    }
};
```

Each object has its own `x`.

### 🔸 With Static (Class Members)

```cpp
class A {
public:
    static int x;
    void increment() {
        x++;
    }
};

int A::x = 0;
```

All objects share the same `x`.

---

## 💼 Interview Preparation Tips

- ✅ **What is the lifetime of a static variable inside a function?**
- ✅ **What is the difference between a static and non-static class variable?**
- ✅ **How does static affect memory usage in C++?**
- ✅ **When is a static object destroyed?**
- ✅ **Can static variables be initialized inside a class?**
- ✅ **How does `static` impact OOP design patterns like Singleton?**
- ✅ **What’s the difference between `const` and `static` in class context?**
- ✅ **Where does the memory of a static variable reside (stack/heap/data)?**

---

## ❌ Common Mistakes or Misunderstandings

- ❗ Assuming a `static` variable gets re-initialized on every function call.
- ❗ Forgetting to define static class members **outside** the class.
- ❗ Believing each object gets its own copy of a static member.
- ❗ Confusing `static` lifetime with global variables (visibility differs).

---

## 🛠️ Tooling & IDE Integration

### 🔹 Visual Studio

- Hovering on a static variable shows its **type and shared status**.
- Class View > Static Members lets you see all static fields/functions.

### 🔹 CLion / Code::Blocks

- Shows `static` scope with icons or color hints.
- Navigate directly to the static definition with "Go to Declaration."

---

## 🧠 Advanced Notes / Behind the Scenes

- Static variables are stored in the **Data Segment** (not stack or heap).
- They support **lazy initialization** (in some compilers) for thread safety.
- Static class members can also be **private** and accessed via static methods.
- `static` functions in C++ (not covered here) restrict visibility to file scope.

---

## 📚 Footnotes / Glossary

- **Static Variable**: A variable that retains its value between function calls.
- **Data Segment**: Memory area where static and global variables reside.
- **Lifetime**: Duration a variable exists in memory.
- **Scope**: The part of the program where a variable is accessible.
- **Constructor**: Special function called during object creation.
- **Destructor**: Special function called during object destruction.
- **Shared Variable**: One memory location used across multiple instances.

---

✅ **Next Chapter Preview**: [Friend Function & Friend Class (Optional Homework)]  
📌 This topic is advanced and not commonly asked in interviews, but great for deep learning.

---
