# Chapter 7: Inheritance in C++

## 🧭 Overview

Inheritance is a fundamental concept in Object-Oriented Programming (OOP) that allows a class (derived class) to acquire properties and behaviors from another class (base class). This promotes **code reusability**, **extensibility**, and helps model real-world relationships effectively.

In this chapter, we will explore:

- The concept and significance of inheritance in C++
- Different types of inheritance: Single, Multilevel, Multiple, Hierarchical, and Hybrid
- Constructor and destructor invocation order
- Access specifiers in inheritance: public, protected, and private
- Common mistakes and best practices
- Tooling and IDE integration
- Advanced notes and behind-the-scenes insights
- Glossary of key terms

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
               Constructor → Base → Derived   Multiple / Hierarchical
               Destructor  → Derived → Base   Hybrid
```

---

## 📚 Detailed Sections

### 1. What is Inheritance?

Inheritance allows a new class to adopt the properties and methods of an existing class. The existing class is referred to as the **base class**, and the new class is called the **derived class**. This mechanism promotes code reusability and establishes a natural hierarchy between classes.

*Example:*

```cpp
class Person {
public:
    string name;
    int age;
};

class Student : public Person {
public:
    int rollNumber;
    void study() {
        cout << name << " is studying." << endl;
    }
};
```

In this example, `Student` inherits attributes `name` and `age` from `Person` and adds its own attribute `rollNumber` and method `study()`.

---

### 2. Why Use Inheritance?

- **Code Reusability:** Inheritance allows the reuse of existing code, reducing redundancy.
- **Extensibility:** New functionalities can be added to existing classes without modifying them.
- **Hierarchy Representation:** It models real-world relationships and hierarchies effectively.
- **Polymorphism Support:** Enables the use of polymorphic behaviors in programs.

---

### 3. Basic Syntax of Inheritance

The syntax for defining a derived class in C++ is:

```cpp
class Base {
    // Base class members
};

class Derived : [access specifier] Base {
    // Derived class members
};
```

- `[access specifier]` determines how the base class members are accessible in the derived class. It can be `public`, `protected`, or `private`.

*Example:*

```cpp
class Person {
public:
    string name;
    int age;
};

class Student : public Person {
public:
    int rollNumber;
};
```

In this example, `Student` publicly inherits from `Person`, meaning all public members of `Person` remain public in `Student`.

---

### 4. Modes of Inheritance

The access specifier used during inheritance affects the accessibility of the base class members in the derived class.

| Mode       | Base Class Members | Derived Class Members | Accessibility in Derived Class |
|------------|--------------------|-----------------------|-------------------------------|
| **Public** | public             | public                | Accessible as public          |
|            | protected          | protected             | Accessible as protected       |
|            | private            | Not inherited         | Not accessible                |
| **Protected** | public          | protected             | Accessible as protected       |
|            | protected          | protected             | Accessible as protected       |
|            | private            | Not inherited         | Not accessible                |
| **Private** | public            | private               | Accessible as private         |
|            | protected          | private               | Accessible as private         |
|            | private            | Not inherited         | Not accessible                |

*Example:*

```cpp
class Base {
public:
    int a;
protected:
    int b;
private:
    int c;
};

class Derived : public Base {
    // a is public
    // b is protected
    // c is not accessible
};
```

---

### 5. Constructor & Destructor Order

When an object of a derived class is created, the constructors and destructors are called in a specific order:

- **Constructor Call Order:** Base class constructor is called first, followed by the derived class constructor.
- **Destructor Call Order:** Derived class destructor is called first, followed by the base class destructor.

*Example:*

```cpp
#include <iostream>
using namespace std;

class Base {
public:
    Base() { cout << "Base Constructor" << endl; }
    ~Base() { cout << "Base Destructor" << endl; }
};

class Derived : public Base {
public:
    Derived() { cout << "Derived Constructor" << endl; }
    ~Derived() { cout << "Derived Destructor" << endl; }
};

int main() {
    Derived obj;
    return 0;
}
```

*Output:*

```
Base Constructor
Derived Constructor
Derived Destructor
Base Destructor
```

---

### 6. Types of Inheritance

C++ supports various types of inheritance to model different relationships. Each type is illustrated below with a diagram and example code.

#### ➤ Single Inheritance

**Definition:** A derived class inherits from only one base class.

**Diagram:**

```
    [Base]
      ↓
    [Derived]
```

**Example:**

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "This animal eats food." << endl;
    }
};

class Dog : public Animal {
public:
    void bark() {
        cout << "The dog barks." << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Inherited from Animal
    myDog.bark(); // Defined in Dog
    return 0;
}
```

*Output:*

```
This animal eats food.
The dog barks.
```

---

#### ➤ Multilevel Inheritance

**Definition:** A derived class inherits from another derived class, forming a "chain" of inheritance.

**Diagram:**

```
    [Animal]
        ↓
    [Mammal]
        ↓
     [Dog]
```

**Example:**

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    void eat() {
        cout << "Animal eats." << endl;
    }
};

class Mammal : public Animal {
public:
    void breathe() {
        cout << "Mammal breathes." << endl;
    }
};

class Dog : public Mammal {
public:
    void bark() {
        cout << "Dog barks." << endl;
    }
};

int main() {
    Dog dog;
    dog.eat();     // From Animal
    dog.breathe(); // From Mammal
    dog.bark();    // From Dog
    return 0;
}
```

---

#### ➤ Multiple Inheritance

**Definition:** A class inherits from more than one base class.

**Diagram:**

```
   [Person]   [Worker]
       ↓        ↓
        → [Engineer]
```

**Example:**

```cpp
#include <iostream>
using namespace std;

class Person {
public:
    void info() {
        cout << "I am a person." << endl;
    }
};

class Worker {
public:
    void work() {
        cout << "I am working." << endl;
    }
};

class Engineer : public Person, public Worker {
public:
    void design() {
        cout << "I am designing." << endl;
    }
};

int main() {
    Engineer eng;
    eng.info();   // From Person
    eng.work();   // From Worker
    eng.design(); // Own method
    return 0;
}
```

---

#### ➤ Hierarchical Inheritance

**Definition:** Multiple classes are derived from a single base class.

**Diagram:**

```
      [Person]
       /   \
 [Student] [Teacher]
```

**Example:**

```cpp
#include <iostream>
using namespace std;

class Person {
public:
    void introduce() {
        cout << "I am a person." << endl;
    }
};

class Student : public Person {
public:
    void study() {
        cout << "I am studying." << endl;
    }
};

class Teacher : public Person {
public:
    void teach() {
        cout << "I am teaching." << endl;
    }
};

int main() {
    Student s;
    Teacher t;
    s.introduce(); s.study();
    t.introduce(); t.teach();
    return 0;
}
```

---

#### ➤ Hybrid Inheritance

**Definition:** A combination of two or more types of inheritance.

**Diagram:**

```
          [Person]
           /    \
   [Student]   [Employee]
           \    /
          [Intern]
```

**Example with Virtual Inheritance (to avoid ambiguity):**

```cpp
#include <iostream>
using namespace std;

class Person {
public:
    void identify() {
        cout << "I am a person." << endl;
    }
};

class Student : virtual public Person {
public:
    void study() {
        cout << "I study." << endl;
    }
};

class Employee : virtual public Person {
public:
    void work() {
        cout << "I work." << endl;
    }
};

class Intern : public Student, public Employee {
public:
    void learn() {
        cout << "I learn as an intern." << endl;
    }
};

int main() {
    Intern i;
    i.identify(); // Only one copy of Person
    i.study();
    i.work();
    i.learn();
    return 0;
}
```

---

## ⚠️ Common Mistakes

- **Not using virtual inheritance** in diamond problems → leads to ambiguity.
- **Wrong access specifiers** in inheritance → can unexpectedly hide members.
- **Forgetting to make destructors virtual** in base classes when using polymorphism.
- **Overriding base functions without `virtual` keyword** can cause unexpected behavior.

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

## 🛠️ Tooling & IDE Integration

- **Visual Studio / VS Code:**
  - Use IntelliSense to visualize class hierarchies.
  - Leverage "Go to Definition" to navigate base and derived classes.
- **CLion / JetBrains:**
  - View class hierarchies in the structure sidebar.
- **UML Plugins:**
  - Use UML plugins to auto-generate class diagrams.
- **Static Analyzers:**
  - Use tools like `clang-tidy` to detect inheritance-related issues.

---

## 🚀 Advanced Notes / Behind the Scenes

- **Virtual Function Table (vtable):**
  - When virtual functions are used, C++ creates a vtable to enable runtime polymorphism.
- **Memory Layout:**
  - Multiple inheritance may lead to complex memory layouts, especially with virtual inheritance.
- **Order of Construction:**
  - C++ always constructs base classes before derived, regardless of declaration order.
- **Slicing Problem:**
  - Object slicing occurs when a derived object is assigned to a base object (by value).

---

## 📚 Glossary

| Term              | Definition                                                                 |
|-------------------|----------------------------------------------------------------------------|
| **Base Class**    | A class whose properties are inherited by another class.                   |
| **Derived Class** | A class that inherits from another class.                                  |
| **Access Specifier** | Defines visibility of base class members in derived class (`public`, etc). |
| **Constructor Order** | The order in which constructors are called (base to derived).           |
| **Destructor Order**  | The order in which destructors are called (derived to base).            |
| **Virtual Inheritance** | Solves the diamond problem by ensuring a single copy of base class.   |

---

## ✅ Summary

- Inheritance promotes code reuse and organization.
- Understand types of inheritance to model different relationships.
- Always be cautious of ambiguities in multiple/hybrid inheritance.
- Prefer composition over inheritance if the relationship isn’t strictly "is-a".
- Use tools and diagrams to keep your class hierarchies clean.

---

✅ **End of Chapter**
