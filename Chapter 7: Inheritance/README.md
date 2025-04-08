# Chapter 7: Inheritance in C++

## 🧭 Overview

Inheritance is one of the four foundational pillars of Object-Oriented Programming (OOP) in C++. It allows one class (child/derived class) to acquire the properties and behaviors of another class (parent/base class). This promotes **code reuse**, **scalability**, and helps model real-world hierarchies.

This chapter covers:
- The basic concept of inheritance in C++
- Constructor and destructor call order
- Modes of inheritance: public, protected, private
- Types of inheritance: single, multilevel
- Practical coding examples
- Interview preparation questions and common pitfalls

---

## 🧠 Mind & Concept Map

```
               ┌────────────────────────┐
               │     Inheritance in     │
               │        C++             │
               └──────────┬─────────────┘
                          │
        ┌─────────────────┼─────────────────────┐
        │                 │                     │
        ▼                 ▼                     ▼
┌─────────────┐   ┌────────────────┐     ┌────────────────────┐
│  Why Use    │   │   Modes of     │     │    Types of        │
│ Inheritance │   │  Inheritance   │     │   Inheritance      │
└────┬────────┘   └─────┬──────────┘     └──────────┬─────────┘
     │                 │                              │
     ▼                 ▼                              ▼
Code Reuse     Public / Protected / Private   Single / Multilevel

              Constructor → Base → Derived
              Destructor  → Derived → Base
```

---

## 📚 Detailed Sections

### 1. What is Inheritance?

- Inheritance allows a class to reuse the properties and methods of another class.
- Example: `Student` can inherit from `Person` and add more attributes.

---

### 2. Why Use Inheritance?

- Avoid code duplication.
- Use common features from base classes.
- Promotes scalability and maintainability.

---

### 3. Basic Syntax of Inheritance

```cpp
class Base {
public:
    string name;
    int age;
};

class Derived : public Base {
public:
    int rollNumber;
};
```

- Use `:` followed by the **mode of inheritance** and base class name.

---

### 4. Modes of Inheritance

| Mode       | Public Members Become | Protected Members Become | Private Members |
|------------|------------------------|---------------------------|------------------|
| Public     | Public in derived      | Protected in derived      | Not Inherited    |
| Protected  | Protected in derived   | Protected in derived      | Not Inherited    |
| Private    | Private in derived     | Private in derived        | Not Inherited    |

---

### 5. Constructor & Destructor Order

- **Constructor Call Order:** Base → Derived
- **Destructor Call Order:** Derived → Base

```cpp
class Person {
public:
    Person() { cout << "Parent Constructor\n"; }
    ~Person() { cout << "Parent Destructor\n"; }
};

class Student : public Person {
public:
    Student() { cout << "Child Constructor\n"; }
    ~Student() { cout << "Child Destructor\n"; }
};
```

---

### 6. Types of Inheritance

#### ➤ Single Inheritance

```cpp
class Person {
public:
    string name;
};

class Student : public Person {
public:
    int roll;
};
```

#### ➤ Multilevel Inheritance

```cpp
class Person {
public:
    string name;
};

class Student : public Person {
public:
    int roll;
};

class Exam : public Student {
public:
    float marks;
};
```

---

## ⚠️ Things to Note

- Private members of base class are **never inherited**.
- Only public and protected members are inherited.
- Base class constructors are not inherited but **called automatically**.
- Always use access specifiers carefully based on design.

---

## 💼 Interview Tips

1. **What gets inherited?**
   - Only public and protected members.
   - Constructors, destructors, and private members are **not** inherited.

2. **Can a derived class access private members of the base?**
   - No, it cannot. Use `protected` if needed in derived class.

3. **What’s the order of constructor/destructor calls?**
   - Constructors: Base → Derived
   - Destructors: Derived → Base

4. **What’s the difference between public and protected inheritance?**
   - Public: keeps base class accessibility as is.
   - Protected: downgrades public members to protected in derived class.

---

## 🧪 Practice Example

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Eating...\n";
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "Barking...\n";
    }
};

int main() {
    Dog d;
    d.eat();   // Inherited from Animal
    d.bark();  // Own function
    return 0;
}
```

---

## ✅ Summary

- Inheritance is essential for reuse and extensibility.
- Understand **modes of inheritance** and **constructor/destructor order**.
- Use proper access specifiers to control visibility.
- Great for modeling real-world "is-a" relationships.

---

## 📌 Next Up

→ In the next chapter, we'll cover **Function Overriding & Virtual Functions** and how they help implement polymorphism in C++.

