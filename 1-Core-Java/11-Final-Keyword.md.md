# 🔒 Final Keyword in Java

> 💡 The **`final`** keyword is used to **restrict modification**. It can be applied to **variables**, **methods**, and **classes** to make your code more secure, immutable, and maintainable.

---

# 🎯 Why Do We Need `final`?

Imagine developing a Banking Application.

- 💰 Account Number should never change.
- 🚗 Car Engine implementation should not be overridden.
- 🏛️ Utility classes should not be inherited.

Java provides the **`final` keyword** to enforce these restrictions.

---

# 📚 Where Can We Use `final`?

The `final` keyword can be applied to:

- 🔹 Variables
- 🔹 Methods
- 🔹 Classes

```text
             final
               │
      ┌────────┼────────┐
      ▼        ▼        ▼
 Variable    Method    Class
```

---

# 🔹 Final Variable

## 📖 Definition

A **final variable** can be assigned **only once**.

After initialization, its value cannot be changed.

---

## 💻 Example

```java
class Employee {

    final int id = 101;

    void display() {

        // id = 102; ❌ Compilation Error

        System.out.println(id);

    }

}
```

### Output

```text
101
```

---

# 🔹 Blank Final Variable

A blank final variable is declared without initialization.

It must be initialized inside the constructor.

---

## 💻 Example

```java
class Employee {

    final int id;

    Employee(int id) {

        this.id = id;

    }

}
```

---

# 🔹 Final Reference Variable

A final reference variable cannot point to another object.

However, the object's internal state can still be modified.

---

## 💻 Example

```java
class Employee {

    String name = "John";

}

public class Demo {

    public static void main(String[] args) {

        final Employee emp = new Employee();

        emp.name = "Alice";      // ✅ Allowed

        // emp = new Employee(); // ❌ Not Allowed

    }

}
```

---

# 🔹 Final Method

## 📖 Definition

A final method **cannot be overridden** by subclasses.

---

## 💻 Example

```java
class Animal {

    final void sound() {

        System.out.println("Animal Sound");

    }

}

class Dog extends Animal {

    // void sound() {} ❌ Compilation Error

}
```

---

# 🔹 Final Class

## 📖 Definition

A final class **cannot be extended (inherited)**.

---

## 💻 Example

```java
final class Employee {

}

// class Manager extends Employee {} ❌ Compilation Error
```

---

# 🌍 Real-World Examples

### 🔒 Final Variable

🆔 Aadhaar Number

Once issued, it cannot be changed.

---

### 🔒 Final Method

🏦 Banking Security Algorithm

No subclass should modify the implementation.

---

### 🔒 Final Class

```java
String
```

The `String` class is **final**.

It cannot be inherited.

This ensures immutability and security.

---

# 📊 Final Variable vs Normal Variable

| Feature | Final Variable | Normal Variable |
|----------|----------------|-----------------|
| Reassignment | ❌ Not Allowed | ✅ Allowed |
| Initialization | Once | Multiple Times |
| Mutability | Fixed | Changeable |

---

# ⚖️ Final Method vs Normal Method

| Final Method | Normal Method |
|---------------|---------------|
| Cannot be overridden | Can be overridden |
| Used for fixed behavior | Used for extensibility |

---

# ⚖️ Final Class vs Normal Class

| Final Class | Normal Class |
|--------------|--------------|
| Cannot be inherited | Can be inherited |
| Provides security | Supports inheritance |

---

# 📌 final vs finally vs finalize()

| Keyword | Purpose |
|----------|---------|
| `final` | Restricts modification |
| `finally` | Executes cleanup code after `try-catch` |
| `finalize()` | Method called by Garbage Collector before object removal *(Deprecated since Java 9 and removed in newer versions)* |

---

# 💻 Example of finally

```java
try {

    int result = 10 / 2;

} finally {

    System.out.println("Cleanup Code");

}
```

Output

```text
Cleanup Code
```

---

# 🌍 Real-World Analogy

Imagine a university.

🎓 Student Roll Number → Final Variable

📚 Examination Rules → Final Method

🏛️ University Constitution → Final Class

These should not be modified.

---

# ❓ Interview Questions

## 1️⃣ What is the `final` keyword?

The `final` keyword is used to restrict modification of variables, methods, and classes.

---

## 2️⃣ Can a final variable be modified?

❌ No.

It can only be assigned once.

---

## 3️⃣ Can a final method be overridden?

❌ No.

---

## 4️⃣ Can a final class be inherited?

❌ No.

---

## 5️⃣ Why is the `String` class final?

To ensure:

- Immutability
- Security
- Thread Safety
- Performance optimizations

---

## 6️⃣ What is the difference between `final`, `finally`, and `finalize()`?

- **final** → Restricts modification.
- **finally** → Executes cleanup code after `try-catch`.
- **finalize()** → Deprecated method that was called before object destruction.

---

# 💡 Best Practices

✅ Use `final` for constants.

```java
public static final double PI = 3.14159;
```

✅ Declare immutable classes as `final`.

✅ Mark methods as `final` when they should not be overridden.

✅ Avoid relying on `finalize()` in modern Java.

---

# 📝 Summary

| Member | Can be Final? | Effect |
|----------|:------------:|--------|
| Variable | ✅ | Value cannot be reassigned |
| Method | ✅ | Cannot be overridden |
| Class | ✅ | Cannot be inherited |

---

# 🎯 Key Takeaway

> The **`final` keyword** helps build **secure, immutable, and maintainable Java applications**. It prevents unwanted modifications to variables, methods, and classes, making it a fundamental concept for both real-world development and Java interviews.