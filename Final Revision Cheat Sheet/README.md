# 📘 OOP in C++ — Ultimate Cheat Sheet for Interviews

---

## 🔥 4 Pillars of OOP

| Concept         | Summary                                                                 |
|----------------|-------------------------------------------------------------------------|
| **Encapsulation** | Wrapping data and functions into a single unit (class). Hides internal details. |
| **Abstraction**   | Hides complex reality, shows only relevant parts. Achieved via interfaces/abstract classes. |
| **Inheritance**   | Acquiring properties of one class into another (reusability).        |
| **Polymorphism**  | One name, many forms (function overloading & overriding).            |

---

## 🧱 C++ Class Basics

```cpp
class MyClass {
private:
    int secret;          // Encapsulation
public:
    void set(int val);   // Interface
    int get();
};
```

---

## 🧰 Constructor & Destructor

```cpp
class A {
public:
    A() { cout << "Constructor\n"; }
    ~A() { cout << "Destructor\n"; }
};
```

- Automatically called when object is created/destroyed.
- Use constructor initializer list for efficiency.

---

## 🧬 Inheritance

```cpp
class Parent {
public:
    void greet() { cout << "Hello!\n"; }
};

class Child : public Parent {
    // Inherits greet()
};
```

- `public`, `protected`, `private` inheritance control access level.
- C++ supports **multiple inheritance**.

---

## 🧭 Polymorphism

### Compile-time (Static)
```cpp
void greet(int);      
void greet(double);   // Function Overloading
```

### Runtime (Dynamic)
```cpp
class Base {
public:
    virtual void show() { cout << "Base\n"; }
};
class Derived : public Base {
public:
    void show() override { cout << "Derived\n"; }
};
```

- Use `virtual` for runtime dispatch.
- Requires `Base* ptr = new Derived();`

---

## 🧼 Abstraction (Pure Virtual)

```cpp
class Shape {
public:
    virtual void draw() = 0;  // Pure virtual
};

class Circle : public Shape {
public:
    void draw() override { cout << "Drawing Circle\n"; }
};
```

- Can't instantiate abstract class.
- Forces child classes to implement abstract methods.

---

## 🧊 Static Keyword

```cpp
class Demo {
public:
    static int count;
};
int Demo::count = 0;
```

- **Static variable**: Shared among all objects.
- **Static function**: Doesn’t access `this` pointer.
- Exists even without object.

---

## 🤝 Friend Function / Class

```cpp
class Box {
private:
    int width;
    friend void printWidth(Box b); // friend function
};

class B;
class A {
    friend class B; // friend class
};
```

- Gives external function/class access to private members.
- **Breaks encapsulation** — use wisely!

---

## 🛠 Important Rules

| Rule Name        | What It Says                                                                 |
|------------------|------------------------------------------------------------------------------|
| Rule of 3        | If you define **destructor**, define copy constructor & copy assignment too. |
| Rule of 5        | Same as Rule of 3 + move constructor + move assignment.                      |
| Rule of 0        | Let compiler manage resources (smart pointers, etc.).                        |

---

## 💡 Common Mistakes

- Not using `virtual` for base class destructor.
- Forgetting `override` keyword in derived class.
- Accessing private members from non-friend/non-member functions.
- Static variables not defined outside class.
- Confusing **function overloading** with **overriding**.

---

## 🧠 Final Interview Tips

✅ Practice writing code by hand  
✅ Always include a virtual destructor in base class  
✅ Use diagrams in whiteboard interviews  
✅ Know differences between stack & heap allocation  
✅ Be ready to answer: **"Why OOP?"** with real-world examples

---


