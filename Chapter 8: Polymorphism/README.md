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
- Encourages **code reuse** and **scalability**.

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

Child class redefines a parent function with the **same signature**:

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

#### 🧬 Run-Time Polymorphism

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

Parent* ptr;
Child c;
ptr = &c;
ptr->show();  // Outputs: Child class
```

---

## 💼 Interview Preparation Tips

- What is polymorphism in C++?
- Differentiate between compile-time and run-time polymorphism.
- Explain constructor overloading with an example.
- What is function overloading?
- How is operator overloading used in C++?
- What is function overriding, and how is it implemented?
- Why is inheritance required for method overriding?
- Can you override constructors in C++? Why or why not?

---

## 🚫 Common Mistakes or Misunderstandings

- ❌ Confusing **overloading** with **overriding**.
- ❌ Forgetting to use the `virtual` keyword for run-time polymorphism.
- ❌ Believing return type alone can distinguish overloaded functions (it can't).
- ❌ Thinking operator overloading changes operator precedence (it doesn’t).
- ❌ Not initializing data members properly in overloaded constructors.

---

## 🧰 Tooling & IDE Integration

- **Visual Studio / CLion / Code::Blocks**
  - IntelliSense / Auto-completion helps detect overloads and overrides.
  - Refactoring tools show function overloads and inherited methods.
  - Run-time debuggers can step into overridden functions.
  - Shows virtual function hierarchies and highlights overridden methods.

---

## 🎓 Advanced Notes / Behind the Scenes

- C++ uses **VTables (Virtual Tables)** to implement **runtime polymorphism**.
- **Name mangling** is used by the compiler to distinguish overloaded functions.
- Function overloading doesn’t support **default arguments** if ambiguity arises.
- Operator overloading uses the `operator` keyword and can be user-defined.
- Constructors cannot be overridden because they are not inherited.

---

## 📘 Footnotes / Glossary

- **Polymorphism** – The ability of an object to take on many forms.
- **Compile-Time Polymorphism** – Resolved during compilation; includes overloading.
- **Run-Time Polymorphism** – Resolved at runtime; includes overriding.
- **VTable** – A mechanism used to support dynamic dispatch of functions.
- **Virtual Function** – A function declared in the base class that can be overridden in derived class.
- **Overloading** – Same function/operator with different parameters.
- **Overriding** – Redefining base class function in derived class with the same signature.

---

✅ **End of Chapter**
