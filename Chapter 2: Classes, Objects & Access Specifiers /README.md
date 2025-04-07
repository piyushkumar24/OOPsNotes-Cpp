# Chapter 2: Classes, Objects & Access Specifiers in C++

## Overview

This chapter introduces the fundamental building blocks of Object-Oriented Programming (OOP) in C++: **Classes**, **Objects**, and **Access Specifiers**.  
You will understand how to define your own data types using classes, create instances (objects), and control access to data members and methods using keywords like `private`, `public`, and `protected`.  

These are essential concepts for modeling real-world entities in software, maintaining data security, and designing robust code.

## Concept Map / Flow Diagram

```
+-------------------------------+
|     Class (User-defined Type)|
+-------------------------------+
| - Data Members (Variables)   |
| - Member Functions (Methods) |
+-------------------------------+
| Access Specifiers:           |
|   - private                  |
|   - public                   |
|   - protected                |
+-------------------------------+
               ↓
+-------------------------------+
|           Object              |
+-------------------------------+
| - Instance of Class           |
| - Uses dot operator           |
+-------------------------------+
```

---

## 1. Classes in C++

A class is a **user-defined data type** that groups data members (variables) and member functions (methods).

**Syntax:**

```cpp
class Teacher {
  // data members
  // member functions
};
```

Functions inside a class are called **member functions** because they belong to the class.

---

## 2. Creating Objects

Objects are instances of a class and can be created in the `main()` function.

```cpp
Teacher t1;       // creates an object t1 of class Teacher
Teacher t2, t3;   // multiple objects
```

Each object has its own copy of the class properties.

---

## 3. Accessing Members with Dot Operator

To access members (data/functions) of a class object, use the **dot (`.`) operator**:

```cpp
t1.name = "Alice";
t1.department = "Computer Science";
t1.subject = "C++";

cout << t1.name;  // prints name
```

---

## 4. Access Specifiers in C++

### What Are Access Specifiers?

Access Specifiers **control the visibility** of class members:

- `private` (default): accessible **only within the class**
- `public`: accessible **inside and outside** the class
- `protected`: accessible **within the class and derived classes** (covered later in inheritance)

### Example:

```cpp
class Teacher {
private:
  double salary; // only accessible inside class

public:
  string name;
  string department;
  string subject;

  void setSalary(double s) {
    salary = s;
  }

  double getSalary() {
    return salary;
  }
};
```

---

## 5. Getters and Setters (Accessing Private Data)

When data is private, it **cannot be accessed directly** from outside the class.  
**Getter and Setter** functions provide a **controlled** way to access or update private values.

### Getter Function

Returns the value of a private data member.

```cpp
double getSalary() {
  return salary;
}
```

### Setter Function

Sets/updates the value of a private data member.

```cpp
void setSalary(double s) {
  salary = s;
}
```

### Why Use Getters and Setters?

- Ensures **data encapsulation**
- Validates inputs before setting them (optional logic)
- Controls how data is exposed to external code

### Usage:

```cpp
Teacher t1;
t1.setSalary(25000);
cout << t1.getSalary();
```

---

## 📌 Practical Example

```cpp
#include <iostream>
using namespace std;

class Teacher {
private:
  double salary; // private member

public:
  string name;
  string department;
  string subject;

  void setSalary(double s) {
    salary = s;
  }

  double getSalary() {
    return salary;
  }
};

int main() {
  Teacher t1;
  t1.name = "Alice";
  t1.department = "Computer Science";
  t1.subject = "C++";
  t1.setSalary(25000);

  cout << "Name: " << t1.name << endl;
  cout << "Department: " << t1.department << endl;
  cout << "Subject: " << t1.subject << endl;
  cout << "Salary: " << t1.getSalary() << endl;

  return 0;
}
```

---

## 💡 Interview Preparation Tips

- What is a class and how is it different from a structure in C++?
- Explain the use of access specifiers: `private`, `public`, `protected`.
- What are getters and setters? Why are they used?
- Can you access a private data member directly from `main()`?
- What happens if no access specifier is mentioned?
- How does encapsulation relate to access specifiers?

---

## ❌ Common Mistakes or Misunderstandings

- Forgetting that **members are private by default** in a class
- Trying to access private members directly (causes compilation error)
- Assuming protected members are accessible from outside the class
- Not using setters/getters when required

---

## 🛠️ Tooling & IDE Integration

**Visual Studio / CLion / Code::Blocks**:

- IntelliSense highlights access errors in real-time
- Code suggestions for member functions
- Use class diagram plugins (e.g., for UML generation)

---

## 📚 Advanced Notes / Behind the Scenes

- When a class member is marked `private`, it is only accessible within the class scope
- Even friend functions or classes can access private members (covered later)
- Access specifiers are checked at **compile time**, so violations throw errors before execution

---

## 📝 Footnotes / Glossary

- **Member Function**: Function defined inside a class  
- **Data Member**: Variable inside a class  
- **Object**: Instance of a class  
- **Getter**: Function to return value of a private member  
- **Setter**: Function to assign value to a private member  
- **Access Specifier**: Keyword controlling visibility (`private`, `public`, `protected`)

---

✅ **End of Chapter**
