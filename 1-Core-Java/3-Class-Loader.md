# 📂 Class Loader in Java

> 💡 **The Class Loader is a JVM component responsible for loading Java classes (`.class` files`) into memory during program execution.**

---

# 🎯 Why Do We Need a Class Loader?

When we write a Java program, it is compiled into **Bytecode (`.class`)**.

The JVM **cannot execute a class unless it is first loaded into memory**.

👉 This responsibility belongs to the **Class Loader**.

---

# 🏗️ Class Loading Process

```text
        ☕ Java Source (.java)
                 │
                 ▼
         🛠️ javac Compiler
                 │
                 ▼
        📦 Bytecode (.class)
                 │
                 ▼
        📂 Class Loader
                 │
                 ▼
        💾 JVM Memory
                 │
                 ▼
        ⚙️ Execution Engine
                 │
                 ▼
          💻 Machine Code
```

---

# 📚 Responsibilities of Class Loader

The Class Loader performs the following tasks:

- 📂 Loads `.class` files into JVM memory.
- ✅ Verifies the bytecode.
- 🔗 Resolves symbolic references.
- 🚀 Initializes classes.

---

# 🏛️ Types of Class Loaders

Java uses **three built-in class loaders**.

```text
           Bootstrap Class Loader
                    ▲
                    │
           Platform Class Loader
                    ▲
                    │
        Application Class Loader
```

---

# 🥇 1. Bootstrap Class Loader

### 📖 Definition

The **Bootstrap Class Loader** is the parent of all class loaders.

It loads **core Java classes** required by every Java application.

### 📦 Loads

```java
java.lang.String
java.lang.Object
java.util.ArrayList
java.util.HashMap
```

### 📍 Location

```text
<JAVA_HOME>/lib
```

### ✅ Examples

```java
String name = "Java";
System.out.println(name);
```

`String` is loaded by the **Bootstrap Class Loader**.

---

# 🥈 2. Platform Class Loader

### 📖 Definition

The **Platform Class Loader** loads platform-specific Java modules and libraries.

### 📦 Examples

```text
java.sql
java.xml
java.logging
```

---

# 🥉 3. Application Class Loader

### 📖 Definition

The **Application Class Loader** loads classes that belong to your application.

Example

```java
public class Employee {

}
```

`Employee.class`

⬇️

Loaded by the **Application Class Loader**.

---

# 🔄 Class Loading Phases

The JVM loads a class in **three phases**.

```text
📂 Loading
      │
      ▼
🔗 Linking
      │
      ▼
🚀 Initialization
```

---

# 📂 1. Loading

The `.class` file is read and loaded into JVM memory.

---

# 🔗 2. Linking

Linking has three steps.

## ✅ Verification

Checks whether the bytecode is valid.

Example:

✔️ Correct bytecode

❌ Corrupted bytecode

---

## 📝 Preparation

Memory is allocated for static variables.

Example

```java
static int age = 10;
```

Memory is reserved before initialization.

---

## 🔄 Resolution

Symbolic references are converted into direct references.

---

# 🚀 3. Initialization

Static variables and static blocks are executed.

Example

```java
class Employee{

    static{

        System.out.println("Class Loaded");

    }

}
```

Output

```text
Class Loaded
```

---

# 🔐 Parent Delegation Model

Java Class Loaders follow the **Parent Delegation Model**.

Instead of loading a class directly, a child loader first asks its parent.

```text
Application Loader
        │
        ▼
Platform Loader
        │
        ▼
Bootstrap Loader
```

### Flow

1️⃣ Application Loader requests a class.

2️⃣ Platform Loader checks.

3️⃣ Bootstrap Loader checks.

4️⃣ If found, the class is loaded.

5️⃣ Otherwise, control returns to the child loader.

---

# 🌍 Real-World Analogy

Imagine a company hierarchy.

👨‍💼 Employee

⬇️ asks

👨‍💼 Manager

⬇️ asks

👨‍💼 CEO

If the CEO knows the answer, the request stops there.

Otherwise, it comes back down the hierarchy.

This is exactly how the **Parent Delegation Model** works.

---

# 💻 Example

```java
public class Main {

    public static void main(String[] args) {

        System.out.println(String.class.getClassLoader());

    }

}
```

Output

```text
null
```

Why?

Because `String` is loaded by the **Bootstrap Class Loader**, which is implemented in native code and is represented as `null`.

---

# ❓ Interview Questions

## 1️⃣ What is a Class Loader?

A JVM component responsible for loading `.class` files into memory.

---

## 2️⃣ How many types of Class Loaders are there?

- 🥇 Bootstrap Class Loader
- 🥈 Platform Class Loader
- 🥉 Application Class Loader

---

## 3️⃣ What is the Parent Delegation Model?

A mechanism where a child Class Loader delegates class loading to its parent before attempting to load the class itself.

---

## 4️⃣ Why is the Bootstrap Class Loader shown as `null`?

Because it is implemented in native code and is not represented as a normal Java object.

---

## 5️⃣ What are the phases of class loading?

- 📂 Loading
- 🔗 Linking
- 🚀 Initialization

---

# 💡 Best Practices

✅ Avoid writing custom Class Loaders unless required.

✅ Follow the Parent Delegation Model.

✅ Do not load the same class multiple times.

✅ Use lazy class loading when appropriate.

---

# 📝 Summary

| Component | Responsibility |
|-----------|----------------|
| 🥇 Bootstrap Loader | Loads Java Core Classes |
| 🥈 Platform Loader | Loads Java Platform Modules |
| 🥉 Application Loader | Loads User Classes |

---

> 🎯 **Key Takeaway**
>
> The **Class Loader** is the gateway between Java bytecode and the JVM. It ensures classes are loaded securely, efficiently, and only when required, following the **Parent Delegation Model**.