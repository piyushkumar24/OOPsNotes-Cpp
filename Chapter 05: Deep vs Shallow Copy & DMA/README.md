# 📘 Chapter 5: Understanding Shallow Copy, Deep Copy & Pass by Reference in C++

This chapter explores how objects are **copied** in C++, particularly the difference between **shallow copy** and **deep copy**, and how memory behavior changes with **pass by reference**. These are critical concepts in object-oriented design when working with **dynamically allocated memory** in classes.

---

## 🗺️ Concept Map 1: High-Level Overview

```
┌───────────────────────┐
│      Object Copying   │
└─────────┬─────────────┘
          │
  ┌───────▼─────────┐
  │ Shallow Copy    │
  └───────┬─────────┘
          │
     ┌────▼────────────┐
     │ Pointer values  │
     │ are copied only │
     └─────────────────┘
          │
          ▼
  🔴 Shared memory problems

          │
  ┌───────▼──────────┐
  │ Deep Copy        │
  └───────┬──────────┘
          │
  ┌───────▼──────────────┐
  │ New memory is        │
  │ allocated & copied   │
  └──────────────────────┘
          │
          ▼
  ✅ Safe, separate copies
```

---

## 🧭 Concept Map 2: Object Copying & Memory Behavior

```
┌──────────────┐     Shallow Copy     ┌──────────────┐
│  Object S1   │ ───────────────────► │  Object S2   │
│ name: Rahul  │                      │ name: Rahul  │
│ cgpaPtr: 555 │                      │ cgpaPtr: 555 │
└─────┬────────┘                      └─────┬────────┘
      │                                   │
      ▼                                   ▼
     Heap Memory at address 555: [8.9] Shared by both

                      VS

┌──────────────┐     Deep Copy        ┌──────────────┐
│  Object S1   │ ───────────────────► │  Object S2   │
│ name: Rahul  │                      │ name: Rahul  │
│ cgpaPtr: 555 │                      │ cgpaPtr: 777 │
└─────┬────────┘                      └─────┬────────┘
      ▼                                   ▼
Heap at 555: [8.9]               Heap at 777: [8.9]
```

---

## 🔍 Detailed Sections

### 1. Introduction to Object Copying in C++

- In C++, copying an object can be done via:
  - **Default Copy Constructor** (provided by compiler)
  - **User-Defined Copy Constructor**
- Two types of copying:
  - 🔹 **Shallow Copy**
  - 🔸 **Deep Copy**

---

### 2. Shallow Copy

- Copies **all member variables** including **pointer addresses**
- Suitable when there’s **no dynamic memory**
- ❗ Dangerous if objects have pointers to heap memory

#### 🔧 Code Example – Shallow Copy
```cpp
class Student {
public:
    string name;
    double* cgpa;

    Student(string n, double c) {
        name = n;
        cgpa = new double;
        *cgpa = c;
    }

    void getInfo() {
        cout << "Name: " << name << ", CGPA: " << *cgpa << endl;
    }
};
```

---


### 3. Deep Copy

- Creates a **new copy** of dynamically allocated memory
- Prevents shared memory issues
- You must define your own copy constructor

#### 🔧 Code Example – Deep Copy
```cpp
class Student {
public:
    string name;
    double* cgpa;

    Student(string n, double c) {
        name = n;
        cgpa = new double(c);
    }

    // Deep Copy Constructor
    Student(const Student& s) {
        name = s.name;
        cgpa = new double(*(s.cgpa));
    }

    void getInfo() {
        cout << "Name: " << name << ", CGPA: " << *cgpa << endl;
    }
};
```

---

### 4. Problem with Shallow Copy

```cpp
Student s1("Rahul", 8.9);
Student s2 = s1; // shallow copy
*s2.cgpa = 9.9;
s1.getInfo(); // ❌ Unexpected output: CGPA = 9.9 instead of 8.9
```

- Both `s1` and `s2` point to the same heap memory!

---

### 5. Safe Deep Copy Solution

```cpp
Student s1("Rahul", 8.9);
Student s2 = s1; // deep copy
*s2.cgpa = 9.9;
s1.getInfo(); // ✅ Outputs: 8.9
s2.getInfo(); // ✅ Outputs: 9.9
```

---

### 6. Pass by Reference

- Avoids creating copies
- Enables modifying the original object directly

#### Syntax:
```cpp
void updateCGPA(Student& s) {
    *(s.cgpa) = 10.0;
}

void printInfo(const Student& s) {
    cout << *(s.cgpa) << endl;
}
```

---

## 💡 Practical Examples

### Before (Shallow Copy):
```cpp
Student s1("Rahul", 8.9);
Student s2 = s1;
*s2.cgpa = 9.9;
```

### After (Deep Copy):
```cpp
Student s1("Rahul", 8.9);
Student s2 = s1;
*s2.cgpa = 9.9;
// s1 remains unaffected
```

---

## 🎯 Interview Preparation Tips

1. Difference between shallow copy and deep copy?
2. Why does shallow copy cause bugs with pointers?
3. What is the role of a copy constructor in C++?
4. What memory issues arise with default copy constructors?
5. Explain the need for deep copy in classes with `new`.
6. What’s the purpose of passing objects by reference?
7. When should you use `const Student&` as a function parameter?
8. What is copied when you pass an object to a function?

---

## ⚠️ Common Mistakes

- ❌ Copying pointer addresses without copying data
- ❌ Not creating deep copy constructors when needed
- ❌ Forgetting `const` in function parameters
- ❌ Thinking `Student s2 = s1;` creates separate copies in all cases

---

## 🛠️ Tooling & IDE Integration

- **Visual Studio, CLion, Code::Blocks:**
  - Use memory inspectors to visualize heap vs stack
  - Watch pointers to catch shared memory bugs
  - Set breakpoints in copy constructors for tracing

---

## 🚀 Advanced Notes / Behind the Scenes

- Compiler-generated copy constructors perform **bitwise** shallow copy
- Deep copy is slower but **safer** in complex programs
- Use the **Rule of Three** in C++:
  - If your class manages dynamic memory:
    - You must implement:
      1. Copy Constructor
      2. Destructor
      3. Copy Assignment Operator

---

## 📚 Glossary

| Term         | Definition |
|--------------|------------|
| **Heap**     | Memory allocated at runtime using `new` |
| **Stack**    | Temporary memory used for function calls and local variables |
| **Shallow Copy** | Copying pointer addresses without duplicating the actual memory |
| **Deep Copy**    | Allocating new memory and copying values from the original object |
| **Pass by Reference** | Passing a variable by address instead of copying it |

---

✅ **End of Chapter**
