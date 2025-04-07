# 💡 Introduction to Object-Oriented Programming (OOP) in C++

This chapter introduces the fundamentals of **Object-Oriented Programming (OOP)** in C++, a powerful programming paradigm that models real-world entities using objects and classes. OOP enhances code **organization**, **reusability**, and **scalability**, making it essential for modern C++ application development.

---

## 🗺️ Concept Map: From Real-World Entities to C++ Classes

```
┌────────────────────┐
│ Real-World Entity  │
│   (e.g., Teacher)  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│      Object         │
│  (Instance of Class)│
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│       Class         │
│ (Template/Blueprint)│
└────────────────────┘

Example:
Class: Teacher
 ├── Properties: name, department, subject, salary
 └── Method: changeDepartment()
```

---

## 📘 Detailed Sections

### 1. What is Object-Oriented Programming (OOP)?

- A programming approach based on **objects** that represent **real-world entities**
- Allows data and behavior to be bundled together
- Encourages:
  - ✅ Code Reusability
  - ✅ Modularity
  - ✅ Abstraction and Encapsulation

> 🧠 Think in terms of **"what it is"** (data + behavior), not just **"what it does"** (functions)

---

### 2. Real-Life Motivation for OOP

**Without OOP:**
```cpp
string t1_name = "Alice";
string t1_department = "Math";
string t2_name = "Bob";
string t2_department = "Physics";
```

**With OOP:**
```cpp
Teacher t1;
t1.name = "Alice";
t1.department = "Math";

Teacher t2;
t2.name = "Bob";
t2.department = "Physics";
```

✅ Results in **cleaner**, **more maintainable**, and **reusable** code

---

### 3. Objects and Classes

| Concept     | Description                                  |
|-------------|----------------------------------------------|
| **Object**  | A real-world entity (e.g., a teacher)        |
| **Class**   | A blueprint/template used to create objects  |

🧠 **Analogy**:  
- Class = Car **Design**  
- Object = A **Car** built from that design

---

### 4. Properties and Methods

#### ➤ **Properties (Attributes)**  
- Represent data related to an object  
- Declared as data members inside a class  
```cpp
string name;
string department;
```

#### ➤ **Methods (Functions inside class)**  
- Define object behavior  
- Implemented as member functions of the class  
```cpp
void changeDepartment(string newDept) {
    department = newDept;
}
```

---

### 5. 🧑‍🏫 C++ Example: Teacher Class

```cpp
#include <iostream>
#include <string>
using namespace std;

class Teacher {
public:
    // Properties
    string name;
    string department;
    string subject;
    double salary;

    // Method
    void changeDepartment(string newDepartment) {
        department = newDepartment;
    }
};
```

---

## 🎯 Interview Preparation Checklist

- 🔹 What is the difference between **class** and **object**?
- 🔹 How do classes promote **code reuse**?
- 🔹 How do you model real-world systems using classes?
- 🔹 Explain and write class for a **Teacher** entity
- 🔹 What are **member functions**?
- 🔹 What are the benefits of OOP in large applications?

---

## ❌ Common Mistakes to Avoid

- 🚫 Forgetting `;` after the class definition
- 🚫 Confusing objects with classes
- 🚫 Declaring all properties in `main()` instead of encapsulating them
- 🚫 Using functions globally rather than within classes

---

## 🛠️ Tooling & IDE Support

- Supported in **Visual Studio Code**, **CLion**, **Code::Blocks**
- Features:
  - ✅ Auto-complete for class members
  - ✅ Syntax highlighting for class methods
  - ✅ Code navigation between declarations and definitions

---

## 🔍 Behind the Scenes: C++ Classes

- Each **object** has its **own copy** of data members
- All objects **share** method definitions
- STL containers like `vector`, `set`, and `map` are **implemented using classes**

---

## 📎 Glossary

| Term          | Description                                     |
|---------------|-------------------------------------------------|
| **Class**     | Blueprint to create similar types of objects    |
| **Object**    | Instance of a class                             |
| **Property**  | Data member representing object state           |
| **Method**    | Member function representing object behavior    |
| **STL**       | Standard Template Library with reusable classes |

---

✅ **End of Chapter**

