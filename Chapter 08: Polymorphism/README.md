# 🧬 Chapter 8: Polymorphism in C++

Polymorphism is the third fundamental pillar of Object-Oriented Programming (OOP). It allows objects in C++ to behave differently based on context, enabling more flexible and maintainable code.

This chapter covers **Compile-Time** and **Run-Time Polymorphism**, showcasing examples like **function overloading**, **constructor overloading**, **operator overloading**, and **method overriding**.

---

## 🗺️ Concept Map

```
+---------------------+
|    Polymorphism     |
+---------------------+
         |
 +--------+---------+
 |                  |
Compile-Time    Run-Time
Polymorphism   Polymorphism
 |                  |
 |              +-----------+
 |              | Overriding|
 |              +-----------+
 |                  |
 |    +-------------------------+
 |    | - Virtual functions     |
 |    | - Inheritance           |
 +--> +-------------------------+
 |
 +--> Overloading
       |
   +-----------+
   | - Constructors
   | - Functions
   | - Operators
   +-----------+
```

---

## 📖 Detailed Sections

### 1. 🔍 What is Polymorphism?

- **Greek origin**:  
  - *Poly* = many  
  - *Morph* = forms  
- It is the ability of an object to take many forms depending on the context.
- Encourages **code reuse**, **extensibility**, and **maintainability**.

---

### 2. ⚙️ Compile-Time Polymorphism (Static)

Decisions are made during compilation.

#### 2.1 🧱 Constructor Overloading

Multiple constructors with different parameters:

```cpp
class Student {
public:
    string name;

    Student() {
        cout << "Non-parameterized constructor\n";
    }

    Student(string name) {
        this->name = name;
        cout << "Parameterized constructor\n";
    }
};
```

**Usage:**

```cpp
Student s1;               // Calls non-parameterized
Student s2("Tony Stark"); // Calls parameterized
```

---

#### 2.2 📦 Function Overloading

Same function name, different parameter lists:

```cpp
class Print {
public:
    void show(int x) {
        cout << "Integer: " << x << endl;
    }

    void show(char c) {
        cout << "Character: " << c << endl;
    }
};
```

**Usage:**

```cpp
Print p;
p.show(10);    // Calls int version
p.show('M');   // Calls char version
```

---

#### 2.3 ➕ Operator Overloading

Same operator behaves differently based on context:

```cpp
string a = "Hello";
string b = " World";
string c = a + b;  // `+` is overloaded for strings
```

*Internally handled by the standard library with custom overloads.*

---

### 3. 🧠 Run-Time Polymorphism (Dynamic)

Decisions made during **runtime**, typically via **inheritance** and **virtual functions**.

#### 3.1 🧬 Function Overriding

Function overriding occurs when a **derived class** provides its own implementation of a function already defined in its **base class**, with the **same signature**.

```cpp
class Parent {
public:
    void show() {
        cout << "Parent class\n";
    }
};

class Child : public Parent {
public:
    void show() {
        cout << "Child class\n";
    }
};
```

**Usage:**

```cpp
Child c;
c.show();  // Outputs: Child class
```

However, this only works **statically**. To enable **dynamic (runtime) dispatch**, we must use `virtual`.

---

### 3.2 🧲 Virtual Functions – Key to Run-Time Polymorphism

When a base class function is marked `virtual`, C++ uses a **VTable** to resolve which function to call at runtime, depending on the actual object type—not the pointer/reference type.

```cpp
class Parent {
public:
    virtual void show() {
        cout << "Parent class\n";
    }
};

class Child : public Parent {
public:
    void show() override {
        cout << "Child class\n";
    }
};
```

**Usage with pointer:**

```cpp
Parent* ptr;
Child c;
ptr = &c;
ptr->show();  // Outputs: Child class
```

Without `virtual`, this would output `Parent class`, even if `ptr` is pointing to a `Child` object.

---

#### 📝 Notes on Virtual Functions

- Declared in base class using the `virtual` keyword.
- Can be **overridden** in derived class.
- **Must have the same signature** to override correctly.
- Often used via **base class pointers or references**.
- Destructors should be `virtual` if a class is used polymorphically.

---

### 🧪 Practical Examples

#### 🧱 Constructor Overloading

```cpp
Student s1;               // Non-parameterized
Student s2("Peter");      // Parameterized
```

#### 📦 Function Overloading

```cpp
Print p;
p.show(100);              // Integer
p.show('A');              // Character
```

#### 🧬 Run-Time Polymorphism with Virtual

```cpp
class Parent {
public:
    virtual void speak() {
        cout << "Speaking from Parent\n";
    }
};

class Child : public Parent {
public:
    void speak() override {
        cout << "Speaking from Child\n";
    }
};

Parent* obj = new Child();
obj->speak();  // Outputs: Speaking from Child
```

---

## 💼 Interview Preparation Tips

- What is polymorphism in C++?
- Differentiate between compile-time and run-time polymorphism.
- Explain constructor overloading with an example.
- What is function overloading?
- How is operator overloading used in C++?
- What is function overriding, and how is it implemented?
- What are virtual functions and why are they important?
- Why must destructors be virtual in polymorphic classes?
- Can constructors be overridden in C++?

---

## 🚫 Common Mistakes or Misunderstandings

- ❌ Confusing **overloading** with **overriding**.
- ❌ Forgetting to use the `virtual` keyword for runtime polymorphism.
- ❌ Believing return type alone distinguishes overloaded functions (it can’t).
- ❌ Expecting base class pointer to call child method without `virtual`.
- ❌ Not declaring destructors as `virtual` in base class when needed.

---

## 🧰 Tooling & IDE Integration

- **Visual Studio / CLion / Code::Blocks**
  - IntelliSense highlights overridden functions.
  - Shows virtual function hierarchies.
  - Auto-completion assists with overloads.
  - Debugger allows stepping into virtual function calls.
  - Refactoring tools help rename across overloads.

---

## 🎓 Advanced Notes / Behind the Scenes

- C++ uses **VTables (Virtual Tables)** to implement **runtime polymorphism**.
- A **vtable pointer (vptr)** is placed in polymorphic objects by the compiler.
- **Name mangling** distinguishes overloaded functions internally.
- Function overloading doesn’t support default arguments that introduce ambiguity.
- **Constructors cannot be overridden**—they are not inherited.
- You can mark virtual functions as `final` to prevent further overriding.

---

## 📘 Footnotes / Glossary

- **Polymorphism** – The ability of an object to take on many forms.
- **Compile-Time Polymorphism** – Resolved during compilation; includes overloading.
- **Run-Time Polymorphism** – Resolved at runtime; includes overriding.
- **Overloading** – Same name, different parameters (function/operator).
- **Overriding** – Redefining base class method in derived class with the same signature.
- **Virtual Function** – Enables runtime dispatch through base class pointers.
- **VTable** – Lookup table used to resolve virtual function calls.
- **vptr** – Pointer to the vtable inside a polymorphic object.

---

✅ **End of Chapter**
