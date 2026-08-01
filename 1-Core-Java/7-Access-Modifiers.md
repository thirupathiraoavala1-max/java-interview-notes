# 🔐 Access Modifiers in Java

> 💡 **Access Modifiers** define the visibility (accessibility) of classes, methods, variables, and constructors. They help control who can access different parts of your code, improving security and encapsulation.

---

# 🎯 Why Do We Need Access Modifiers?

Imagine developing a **Banking Application**.

- 💰 Balance should not be directly modified by anyone.
- 🔒 Password should remain private.
- 🌍 Public APIs should be accessible to users.

👉 Access Modifiers help enforce these rules.

---

# 📚 Types of Access Modifiers

Java provides **four access modifiers**.

| Modifier | Same Class | Same Package | Subclass | Other Package |
|----------|:----------:|:------------:|:--------:|:-------------:|
| 🟢 public | ✅ | ✅ | ✅ | ✅ |
| 🟡 protected | ✅ | ✅ | ✅ | ❌* |
| 🔵 default *(package-private)* | ✅ | ✅ | ❌ | ❌ |
| 🔴 private | ✅ | ❌ | ❌ | ❌ |

> 📌 `protected` members are accessible in subclasses even if they are in a different package (through inheritance).

---

# 🟢 1. public

## 📖 Definition

A `public` member can be accessed **from anywhere**.

---

## 💻 Example

```java
public class Employee {

    public String name = "John";

}
```

Usage

```java
Employee emp = new Employee();

System.out.println(emp.name);
```

✅ Accessible from any package.

---

# 🟡 2. protected

## 📖 Definition

A `protected` member can be accessed:

- Inside the same class
- Within the same package
- In subclasses (even in different packages)

---

## 💻 Example

```java
class Animal {

    protected void sound() {

        System.out.println("Animal Sound");

    }

}
```

```java
class Dog extends Animal {

    void bark() {

        sound();

    }

}
```

---

# 🔵 3. default (Package-Private)

## 📖 Definition

If no access modifier is specified, Java assigns **default (package-private)** access.

It can only be accessed within the same package.

---

## 💻 Example

```java
class Employee {

    String department = "IT";

}
```

Accessible only inside the same package.

---

# 🔴 4. private

## 📖 Definition

A `private` member can only be accessed within the same class.

This is commonly used for **Encapsulation**.

---

## 💻 Example

```java
class Employee {

    private double salary = 50000;

}
```

Accessing it directly will result in a compilation error.

---

## ✅ Correct Way

```java
class Employee {

    private double salary;

    public double getSalary() {

        return salary;

    }

    public void setSalary(double salary) {

        this.salary = salary;

    }

}
```

---

# 🌍 Real-World Analogy

Imagine a company.

| Role | Access Modifier |
|------|-----------------|
| 🌍 Reception | public |
| 🏢 Employees | default |
| 👨‍💼 Managers | protected |
| 🔒 Personal Locker | private |

---

# 📊 Visual Representation

```text
                 🌍 public
      +----------------------------+
      |        🟡 protected         |
      |   +--------------------+   |
      |   | 🔵 default         |   |
      |   | +--------------+   |   |
      |   | | 🔴 private   |   |   |
      |   | +--------------+   |   |
      |   +--------------------+   |
      +----------------------------+
```

---

# 🧩 Access Modifiers on Classes

Only two access modifiers are allowed for **top-level classes**.

| Modifier | Allowed |
|----------|----------|
| public | ✅ |
| default | ✅ |
| protected | ❌ |
| private | ❌ |

---

# ⚖️ public vs private

| public | private |
|---------|----------|
| Accessible everywhere | Accessible only within the class |
| Used for APIs | Used for sensitive data |
| Less restrictive | Most restrictive |

---

# ⚖️ protected vs default

| protected | default |
|------------|---------|
| Same package + subclasses | Same package only |
| Supports inheritance | No access outside the package |

---

# 💻 Example

```java
class Employee {

    public String name = "John";

    protected int age = 30;

    String department = "IT";

    private double salary = 50000;

}
```

| Variable | Access Modifier |
|-----------|-----------------|
| name | public |
| age | protected |
| department | default |
| salary | private |

---

# 🎯 When to Use Which?

| Situation | Recommended Modifier |
|------------|----------------------|
| Public API | 🟢 public |
| Sensitive Fields | 🔴 private |
| Inheritance Support | 🟡 protected |
| Internal Package Classes | 🔵 default |

---

# ❓ Interview Questions

## 1️⃣ How many access modifiers are available in Java?

✅ Four:

- public
- protected
- default
- private

---

## 2️⃣ Which is the most restrictive access modifier?

✅ `private`

---

## 3️⃣ Which access modifier supports inheritance?

✅ `protected`

---

## 4️⃣ Can a top-level class be private?

❌ No.

Top-level classes can only be:

- `public`
- `default`

---

## 5️⃣ Why are fields usually declared private?

To achieve **Encapsulation** by preventing direct access and providing controlled access through getter and setter methods.

---

# 💡 Best Practices

✅ Keep fields `private`.

✅ Expose only required methods as `public`.

✅ Use `protected` only when inheritance is intended.

✅ Use `default` for package-internal implementation details.

✅ Follow the principle of **least privilege**—grant only the minimum required access.

---

# 📝 Summary

| Modifier | Scope |
|----------|-------|
| 🟢 public | Everywhere |
| 🟡 protected | Same Package + Subclasses |
| 🔵 default | Same Package |
| 🔴 private | Same Class Only |

---

# 🎯 Key Takeaway

> **Access Modifiers** control the visibility of Java classes and members, helping developers build secure, maintainable, and well-encapsulated applications. Choosing the appropriate modifier improves code quality and prevents unintended access.