# 📘 Chapter 6: Destructor in C++ – Memory Management in OOP

## 🔍 Overview

In this chapter, we explore the concept of **destructors** in C++. Destructors play a crucial role in **automatic memory cleanup** for objects, especially when dealing with **dynamically allocated memory** using `new`. Understanding destructors helps avoid **memory leaks**, which are a serious concern in real-world software and are commonly tested in technical interviews.

---

## 🗺️ Concept Map: Memory Management with Destructors

```
┌──────────────┐
│  Heap Memory │
└────┬─────────┘
     │ Allocated via `new`
     ▼
┌──────────────┐
│  Pointer PTR │ ──▶ [Value at 0x100: 55]
└────┬─────────┘
     │
     ▼
Use `delete PTR` to deallocate memory
     ▼
┌────────────────────┐
│ Destructor gets    │
│ called automatically│
└────────────────────┘
```

---

## 📘 Detailed Sections

### 1. Dynamic Memory Allocation in C++

- When you use `new` to allocate memory:
  ```cpp
  int* ptr = new int(55);
  ```
- It stores the value `55` at some heap address, say `0x100`
- The pointer `ptr` stores the address `0x100`
- To free the allocated memory, use:
  ```cpp
  delete ptr;
  ```

🔎 **Important:**
- `delete ptr;` does **not** delete the pointer itself
- It **deletes the memory** that the pointer is pointing to

---

### 2. What is a Destructor?

- A **special member function** in a class
- Called **automatically** when an object **goes out of scope**
- Responsible for **deallocating dynamic memory** or doing cleanup

#### Syntax:
```cpp
class Student {
public:
    ~Student() {
        cout << "Hi, I delete everything!" << endl;
    }
};
```
- The tilde `~` before the class name indicates it’s a **destructor**

---

### 3. Why Use Destructors?

- Prevent **memory leaks** when using dynamic allocation:
  ```cpp
  class Student {
      int* cgpa;
  public:
      Student() {
          cgpa = new int(9);
      }
      ~Student() {
          delete cgpa;
      }
  };
  ```
- The destructor ensures that the dynamically allocated memory is freed

---

### 4. Destructor Behavior

- Automatically called **when object goes out of scope**
- No need to call destructor manually
- Works like a cleanup crew for your class objects

#### Example Execution Flow:
```cpp
int main() {
    Student s1;
    // s1 constructor runs
    // s1 getInfo() runs
} // s1 destructor runs automatically
```

🧠 **Note:**
- If you don't write a destructor, C++ provides a default one
- But if you’ve used `new`, you must write your own to use `delete`

---

## 🧪 Practical Example

### Code:
```cpp
#include <iostream>
using namespace std;

class Student {
    int* cgpa;
public:
    Student() {
        cgpa = new int(9);
    }

    void getInfo() {
        cout << "CGPA: " << *cgpa << endl;
    }

    ~Student() {
        cout << "Destructor called. Memory freed." << endl;
        delete cgpa;
    }
};

int main() {
    Student s1;
    s1.getInfo();
    return 0;
}
```

### Output:
```
CGPA: 9
Destructor called. Memory freed.
```

---

## 🎯 Interview Preparation Tips

1. What is a destructor in C++?
2. How does a destructor differ from a constructor?
3. Can destructors take arguments?
4. When is the destructor automatically called?
5. What happens if you don't define a destructor when using `new`?
6. What’s the difference between deleting a pointer and the memory it points to?
7. What is a memory leak and how can destructors help prevent it?
8. Can you manually call a destructor in C++?

---

## ❌ Common Mistakes or Misunderstandings

- ❗ Thinking `delete ptr;` deletes the pointer variable
- ❗ Forgetting to free heap memory allocated using `new`
- ❗ Not writing a destructor when using dynamic allocation
- ❗ Assuming destructors are optional in all cases
- ❗ Not understanding the scope and lifecycle of objects

---

## 🛠️ Tooling & IDE Integration

- **Visual Studio / VS Code**:
  - Automatically highlights destructors in class views
  - Shows memory usage in debugger
- **CLion**:
  - Destructors appear in the structure pane
  - Integrated memory leak detection

🔧 Pro Tip: Use Valgrind or built-in memory profilers to detect leaks in projects

---

## 🧠 Advanced Notes / Behind the Scenes

- Destructors are **non-inheritable** and **non-overloaded**
- Automatically called in **reverse order** of constructor execution
- If your class has pointers, always define a custom destructor
- Helps with **RAII (Resource Acquisition Is Initialization)** pattern

---

## 📚 Footnotes / Glossary

- **Heap Memory**: Memory allocated during runtime using `new`
- **Destructor**: A method called to clean up when an object goes out of scope
- **Memory Leak**: Unused memory that is never released back to the system
- **RAII**: A C++ programming idiom where resource allocation is tied to object lifetime

---
