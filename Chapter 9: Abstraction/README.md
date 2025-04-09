# 📘 Chapter 9: Abstraction in C++

---

## 🧠 Overview

Abstraction is one of the core principles of Object-Oriented Programming (OOP). It refers to the concept of hiding unnecessary implementation details from the user and exposing only the relevant parts of an object or system. In C++, abstraction is achieved using access specifiers and abstract classes with pure virtual functions. This chapter dives into how abstraction works, how it relates to real-world modeling, and how to implement it in C++.

---

## 🗺️ Concept Map

```
+------------------------+
|      Abstraction       |
+------------------------+
        |
        | Achieved by
        ↓
+------------------------+       +---------------------------+
|  Access Specifiers     |       |  Abstract Classes         |
+------------------------+       +---------------------------+
| - private              |       | - Have pure virtual       |
| - protected            |       |   functions               |
| - public               |       | - Cannot be instantiated  |
+------------------------+       +---------------------------+
```

---

## 📚 Detailed Sections

### 1. 🔐 Access Specifiers and Abstraction

- Access specifiers help in controlling the visibility of class members.
- **private**: Hides data (used for sensitive information).
- **public**: Exposes relevant methods or properties.
- **protected**: Acts like private but allows access to derived classes.
- These specifiers help implement **information hiding** which is a key part of abstraction.

#### Example:
```cpp
class Employee {
private:
    int salary; // sensitive data
public:
    void setSalary(int s) { salary = s; }
    int getSalary() { return salary; }
};
```

---

### 2. 🧰 What Is an Abstract Class?

- A class that contains at least one **pure virtual function**.
- It serves as a blueprint for other classes.
- Cannot be instantiated directly.
- Enforces certain functions to be implemented in derived classes.

#### Syntax:
```cpp
class Shape {
public:
    virtual void draw() = 0; // pure virtual function
};
```

- Any class inheriting `Shape` **must** override the `draw()` function.

---

### 3. 🧪 Pure Virtual Functions

- Declared using the syntax `= 0` in the base class.
- They indicate that derived classes must provide a concrete implementation.
- The presence of even one pure virtual function makes a class abstract.

#### Example:
```cpp
class Shape {
public:
    virtual void draw() = 0; // pure virtual function
};
```

---

### 4. 🧱 Implementing Abstraction with Abstract Classes

```cpp
class Shape {
public:
    virtual void draw() = 0; // pure virtual function
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle" << endl;
    }
};

int main() {
    // Shape s; ❌ Error: Cannot instantiate abstract class
    Circle c;
    c.draw(); // ✅ Outputs: Drawing Circle
}
```

---

### 5. 🧭 Abstract Class as a Blueprint

- Abstract classes act as templates or interfaces for derived classes.
- Think of `Shape` as an idea: Circle, Rectangle, Square — all inherit it and define their own versions of `draw()`.

```cpp
class Rectangle : public Shape {
public:
    void draw() override {
        cout << "Drawing Rectangle" << endl;
    }
};
```

---

## ✅ Practical Examples

### 🎯 Use Case: Drawing Different Shapes

```cpp
class Shape {
public:
    virtual void draw() = 0; // pure virtual
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle\n";
    }
};

class Square : public Shape {
public:
    void draw() override {
        cout << "Drawing Square\n";
    }
};

int main() {
    Circle c;
    Square s;

    c.draw(); // Drawing Circle
    s.draw(); // Drawing Square
}
```

---

## 🎯 Interview Preparation Tips

1. What is abstraction in C++ and how is it implemented?
2. What are access specifiers in C++ and how do they help with abstraction?
3. What is an abstract class? Can it be instantiated?
4. What is a pure virtual function?
5. How does abstraction differ from encapsulation?
6. Can a class be abstract without having any data members?
7. What error do you get when you try to instantiate an abstract class?
8. How is abstraction useful in real-world modeling?

---

## ⚠️ Common Mistakes or Misunderstandings

- ❌ Trying to instantiate an abstract class.
- ❌ Forgetting to override all pure virtual functions in derived classes.
- ❌ Confusing abstraction with encapsulation (they are related but different).
- ❌ Using the `virtual` keyword in derived class unnecessarily (not needed if base class already has it).
- ❌ Believing abstraction is only about hiding — it's also about showing only what's necessary.

---

## 🛠️ Tooling & IDE Integration

- **Visual Studio / CLion**:
  - Syntax highlighting for `virtual` and `= 0`.
  - Intellisense shows abstract methods in base class.
  - Compile-time errors if abstract classes are misused.

- **Error Message Example**:
  ```
  cannot declare variable ‘s’ to be of abstract type ‘Shape’
  ```

---

## 🧠 Advanced Notes / Behind the Scenes

- Abstract classes are not required to have only pure virtual functions.
- A class can have both implemented and pure virtual methods.
- Virtual tables (vtable) are used internally to achieve dynamic dispatch.
- Abstract classes define contracts or interfaces — this is a form of polymorphism.

---

## 📘 Footnotes / Glossary

- **Abstraction**: The act of hiding implementation details and exposing only the essential features.
- **Access Specifier**: Keywords like `private`, `protected`, `public` that control visibility.
- **Abstract Class**: A class with at least one pure virtual function.
- **Pure Virtual Function**: A function that is declared with `= 0` and has no implementation in the base class.
- **Instantiation**: The process of creating an object from a class.
- **Blueprint**: A model or template for creating new derived classes.

---
