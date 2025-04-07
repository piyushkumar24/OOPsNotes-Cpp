# Chapter 3: OOP Pillars & Encapsulation in C++

## Overview  
This chapter introduces the four foundational pillars of Object-Oriented Programming (OOP) in C++ with a deep dive into **Encapsulation**. These pillars—Encapsulation, Abstraction, Inheritance, and Polymorphism—form the conceptual core of OOP. Understanding them enables developers to build modular, secure, and scalable code.

We focus here on **Encapsulation**, which is about binding data and methods into a single unit (class), ensuring data protection and abstraction.

---

## Concept Map: Pillars of OOP  
```
┌────────────────────────────┐
│      OOP Pillars in C++    │
└────────────────────────────┘
        ↓         ↓         ↓         ↓
 ┌────────────┐ ┌──────────┐ ┌────────────┐ ┌──────────────┐
 │Encapsulation│ │Abstraction│ │Inheritance │ │Polymorphism  │
 └────────────┘ └──────────┘ └────────────┘ └──────────────┘
```

---

## 1. Introduction to OOP Pillars

- OOP in C++ is based on four main principles (pillars):
  - **Encapsulation**: Bundling data & methods in a class.
  - **Abstraction**: Hiding complex implementation from the user.
  - **Inheritance**: Deriving new classes from existing ones.
  - **Polymorphism**: Same function behaves differently on different objects.

> ✅ In this chapter, we’ll explore **Encapsulation** in detail.

---

## 2. What is Encapsulation?

- Encapsulation = Wrapping up of data (properties) and member functions into a **single unit** (class).
- Think of it as a **capsule** that binds data and behavior.

### 🔍 Definition
> "Encapsulation is the wrapping up of data and functions into a single unit."

### ✍️ Real Meaning
- You create a `class` and put:
  - **Data Members** (properties)
  - **Member Functions** (methods)
- Together, they form a **capsule** = Encapsulation

---

## 3. Why Use Encapsulation?

- Ensures **data hiding** through access specifiers (e.g., `private`)
- Protects sensitive information (like passwords, account balance)
- Encourages modular, maintainable code
- Enables access control using **getters** and **setters**

---

## 4. Implementing Encapsulation in C++

### 🔐 Access Specifiers
- `private`: Members accessible only inside the class.
- `public`: Accessible from anywhere.
- `protected`: Accessible in the class and derived classes.

### 📦 Encapsulation = Class with private data + public methods

```cpp
class Account {
private:
    int accountID;
    string username;
    double balance;
    string password;

public:
    void setBalance(double b) {
        balance = b;
    }

    double getBalance() {
        return balance;
    }

    void setPassword(string p) {
        password = p;
    }
};
```

---

## 5. Practical Example: Data Hiding in Action

```cpp
#include <iostream>
using namespace std;

class Account {
private:
    int accountID;
    string username;
    double balance;
    string password;

public:
    void setData(int id, string user, double bal, string pass) {
        accountID = id;
        username = user;
        balance = bal;
        password = pass;
    }

    void displayInfo() {
        cout << "Account ID: " << accountID << endl;
        cout << "Username: " << username << endl;
        // Not showing password or balance directly
    }

    double getBalance() {
        return balance;
    }
};

int main() {
    Account user1;
    user1.setData(101, "techcoder", 50000.75, "secure@123");

    user1.displayInfo();
    cout << "Balance: " << user1.getBalance() << endl;

    return 0;
}
```

---

## 💼 Interview Preparation Tips

- What is Encapsulation? Explain with an example.
- How does C++ support encapsulation?
- How is encapsulation different from abstraction?
- What are access specifiers? Which one helps with data hiding?
- Can private members be accessed outside the class?
- Why use getters and setters instead of public variables?

---

## 🚫 Common Mistakes or Misunderstandings

- ❌ Trying to access private members directly (compilation error)
- ❌ Thinking `private` and `protected` mean the same
- ❌ Forgetting to use getter/setter for private data
- ❌ Assuming encapsulation is only about access specifiers (it's also about design!)

---

## 🧰 Tooling & IDE Integration

- **Visual Studio / Code::Blocks / CLion:**
  - IntelliSense warns about private access
  - Code suggestions auto-complete method names
  - UML plugins available for visualizing encapsulation

---

## 🎓 Advanced Notes / Behind the Scenes

- Even though private members are hidden, **friend classes/functions** (covered later) can still access them.
- Access specifiers are enforced at **compile time**.
- Proper encapsulation = safer APIs + less chance of bugs from external access.

---

## 📘 Footnotes / Glossary

- **Class**: User-defined data type that bundles data + methods.
- **Encapsulation**: Binding data and behavior together.
- **Access Specifiers**: Control visibility (`private`, `public`, `protected`)
- **Getter**: Function that returns private data.
- **Setter**: Function that modifies private data.
- **Data Hiding**: Restricting access to internal class details.

---
