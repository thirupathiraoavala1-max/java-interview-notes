# 🧩 Object-Oriented Programming (OOP) Concepts

> 💡 **Object-Oriented Programming (OOP)** is a programming paradigm that organizes software around **objects**, making applications modular, reusable, scalable, and easy to maintain.

---

# 🎯 Why OOP?

Imagine building an **Employee Management System**.

Without OOP:

- ❌ Duplicate code
- ❌ Difficult maintenance
- ❌ Poor scalability

With OOP:

- ✅ Code Reusability
- ✅ Better Security
- ✅ Easy Maintenance
- ✅ Real-World Modeling

---

# 🌍 Real-World Example

Think of a **Car** 🚗

A car has:

- Properties → Color, Brand, Speed
- Behaviors → Start, Stop, Accelerate

Similarly, in Java:

```java
class Car {

    String brand;
    String color;

    void start() {}

    void stop() {}

}
```

The **Car** is an Object.

---

# 🏗️ Four Pillars of OOP

```text
                🧩 OOP
                 │
     ┌───────────┼───────────┐
     │           │           │
     ▼           ▼           ▼
🔒 Encapsulation 🧬 Inheritance
     │                       │
     └──────────────┬────────┘
                    ▼
             🎭 Polymorphism
                    │
                    ▼
              🎨 Abstraction
```

---

# 🔒 1. Encapsulation

## 📖 Definition

Encapsulation means **wrapping data and methods together into a single unit (class)** and restricting direct access to data.

Use **private fields** with **public getters and setters**.

---

## 💻 Example

```java
class Employee {

    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

}
```

---

## 🌍 Real-World Example

🏦 ATM Machine

You can withdraw money using buttons.

You cannot directly access the internal banking system.

---

## ✅ Advantages

- Data Security
- Better Control
- Easy Maintenance

---

# 🧬 2. Inheritance

## 📖 Definition

Inheritance allows one class to acquire the properties and behaviors of another class.

Use the **extends** keyword.

---

## 💻 Example

```java
class Animal {

    void eat() {
        System.out.println("Eating...");
    }

}

class Dog extends Animal {

    void bark() {
        System.out.println("Barking...");
    }

}
```

---

## 🌍 Real-World Example

👨 Parent

⬇

👦 Child

A child inherits many characteristics from the parent.

---

## ✅ Advantages

- Code Reusability
- Easy Maintenance
- Less Duplication

---

# 🎭 3. Polymorphism

## 📖 Definition

Polymorphism means **one interface, many implementations**.

Java supports:

- Compile-Time Polymorphism (Method Overloading)
- Runtime Polymorphism (Method Overriding)

---

# 🔹 Method Overloading

Same method name with different parameters.

```java
class Calculator {

    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }

}
```

---

# 🔹 Method Overriding

Subclass provides its own implementation.

```java
class Animal {

    void sound() {
        System.out.println("Animal Sound");
    }

}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }

}
```

---

## 🌍 Real-World Example

🚗 Vehicle

Car → Starts differently

Bike → Starts differently

Truck → Starts differently

Same operation.

Different implementation.

---

# 🎨 4. Abstraction

## 📖 Definition

Abstraction hides implementation details and shows only the essential functionality.

Java supports abstraction using:

- Abstract Classes
- Interfaces

---

# 💻 Abstract Class Example

```java
abstract class Animal {

    abstract void sound();

}

class Dog extends Animal {

    @Override
    void sound() {
        System.out.println("Bark");
    }

}
```

---

# 💻 Interface Example

```java
interface Payment {

    void pay();

}

class CreditCardPayment implements Payment {

    @Override
    public void pay() {
        System.out.println("Paid using Credit Card");
    }

}
```

---

## 🌍 Real-World Example

🚗 Car

You know how to drive it.

You don't need to know how the engine works internally.

---

# 📊 OOP Summary

| Concept | Purpose |
|----------|----------|
| 🔒 Encapsulation | Data Hiding |
| 🧬 Inheritance | Code Reuse |
| 🎭 Polymorphism | Multiple Behaviors |
| 🎨 Abstraction | Hide Complexity |

---

# ⚖️ Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|----------|----------------|-----------|
| Methods | Abstract + Concrete | Abstract (and default/static methods in modern Java) |
| Constructors | ✅ Yes | ❌ No |
| Variables | Instance & Static | `public static final` Constants |
| Inheritance | Single | Multiple |

---

# 🌍 OOP in Real Projects

| OOP Concept | Example |
|-------------|---------|
| 🔒 Encapsulation | DTO, Entity |
| 🧬 Inheritance | BaseEntity extends Object |
| 🎭 Polymorphism | Payment Strategies |
| 🎨 Abstraction | Service Interfaces |

---

# ❓ Interview Questions

### 1️⃣ What are the four pillars of OOP?

- 🔒 Encapsulation
- 🧬 Inheritance
- 🎭 Polymorphism
- 🎨 Abstraction

---

### 2️⃣ Difference between Overloading and Overriding?

| Overloading | Overriding |
|--------------|------------|
| Same Class | Parent & Child |
| Compile Time | Runtime |
| Different Parameters | Same Signature |

---

### 3️⃣ Difference between Abstract Class and Interface?

Abstract Class:
- Can have constructors
- Can contain both abstract and concrete methods

Interface:
- Supports multiple inheritance
- Defines a contract that implementing classes must follow

---

### 4️⃣ Why is Encapsulation important?

It protects data by restricting direct access and provides controlled access through methods.

---

### 5️⃣ Why is Polymorphism useful?

It allows writing flexible and extensible code by programming against interfaces or parent types.

---

# 💡 Best Practices

✅ Prefer composition over inheritance where appropriate.

✅ Keep fields private.

✅ Program to interfaces, not implementations.

✅ Use inheritance only when an "is-a" relationship exists.

✅ Keep classes focused on a single responsibility.

---

# 📝 Summary

| Pillar | Key Benefit |
|---------|-------------|
| 🔒 Encapsulation | Data Security |
| 🧬 Inheritance | Code Reuse |
| 🎭 Polymorphism | Flexibility |
| 🎨 Abstraction | Simplicity |

---

# 🎯 Key Takeaway

> OOP enables developers to build **modular, reusable, secure, and maintainable applications** by combining **Encapsulation, Inheritance, Polymorphism, and Abstraction**. These concepts form the foundation of Java and are heavily used in frameworks like **Spring Boot** and **Hibernate**.