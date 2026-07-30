# 🏗️ JVM Architecture

> 💡 **JVM (Java Virtual Machine)** is the heart of Java. It executes Java Bytecode and makes Java **Platform Independent**.

---

# 📌 JVM Architecture Overview

```text
               ☕ Java Source Code (.java)
                        │
                        ▼
               🛠️ Java Compiler (javac)
                        │
                        ▼
                 📦 Bytecode (.class)
                        │
                        ▼
              🚀 Java Virtual Machine
                        │
 ┌──────────────────────┼──────────────────────┐
 │                      │                      │
 ▼                      ▼                      ▼
📂 Class Loader    💾 Runtime Memory     ⚙️ Execution Engine
                                              │
                                              ▼
                                     🔗 Native Interface (JNI)
                                              │
                                              ▼
                                      🖥️ Native Libraries
```

---

# 📂 Components of JVM

| Component | Responsibility |
|------------|----------------|
| 📂 Class Loader | Loads Class Files |
| 💾 Runtime Data Area | Stores Program Data |
| ⚙️ Execution Engine | Executes Bytecode |
| 🔗 JNI | Connects Java with Native Code |
| 🖥️ Native Libraries | Platform Specific Libraries |

---

# 📂 1. Class Loader

## 🎯 Responsibility

- ✅ Loads `.class` files
- ✅ Verifies Bytecode
- ✅ Resolves References
- ✅ Initializes Classes

---

## 📚 Types of Class Loaders

### 🥇 Bootstrap Class Loader

Loads Core Java Classes.

Examples

```java
java.lang.String
java.lang.Object
java.util.ArrayList
```

---

### 🥈 Platform Class Loader

Loads Platform Libraries.

Example

```text
java.sql
java.xml
```

---

### 🥉 Application Class Loader

Loads User Defined Classes.

```java
public class Employee{

}
```

---

# 💾 Runtime Data Area

Runtime Memory is divided into **5 Parts**

| Memory Area | Shared | Stores |
|--------------|---------|---------|
| 🟦 Method Area | ✅ Yes | Class Metadata |
| 🟩 Heap | ✅ Yes | Objects |
| 🟨 Stack | ❌ No | Local Variables |
| 🟧 PC Register | ❌ No | Current Instruction |
| 🟥 Native Stack | ❌ No | Native Methods |

---

# 🟦 Method Area

Stores

- 📌 Class Information
- 📌 Static Variables
- 📌 Constant Pool
- 📌 Method Information

---

# 🟩 Heap Memory

Stores Objects.

```java
Employee emp = new Employee();
```

📦 Object is created inside **Heap Memory**

### ⭐ Managed By

Garbage Collector

---

# 🟨 Java Stack

Each Thread has its own Stack.

Stores

- Local Variables
- Method Calls
- Intermediate Results

Example

```java
public void display(){

    int age = 25;

}
```

`age` is stored in Stack.

---

# 🟧 PC Register

Stores

👉 Address of Current JVM Instruction

Each Thread has its own PC Register.

---

# 🟥 Native Method Stack

Stores Native Method Information.

Example

```java
System.loadLibrary("example");
```

---

# ⚙️ Execution Engine

Execution Engine executes Bytecode.

It contains

- 🟢 Interpreter
- 🔵 JIT Compiler
- 🟣 Garbage Collector

---

## 🟢 Interpreter

Reads Bytecode

➡️ One Line at a Time

### 👍 Advantage

Fast Startup

### 👎 Disadvantage

Slow Execution

---

## 🔵 JIT Compiler

**Just-In-Time Compiler**

Converts Frequently Executed Bytecode

➡️ Native Machine Code

### Benefits

✅ Faster Execution

✅ Better Performance

---

## 🟣 Garbage Collector

Automatically Removes Unused Objects.

```java
Employee emp = new Employee();

emp = null;
```

Object becomes eligible for Garbage Collection.

---

# 🔗 JNI (Java Native Interface)

Allows Java to call Native Languages.

Supported Languages

- C
- C++

Example

```java
public native void display();
```

---

# 🖥️ Native Libraries

Examples

- Windows ➜ DLL
- Linux ➜ SO

---

# 🚀 JVM Execution Flow

```text
☕ Java Source (.java)
          │
          ▼
🛠️ Compiler (javac)
          │
          ▼
📦 Bytecode (.class)
          │
          ▼
📂 Class Loader
          │
          ▼
💾 Runtime Memory
          │
          ▼
⚙️ Execution Engine
          │
          ▼
🖥️ Machine Code
```

---

# 🌍 Real World Analogy

🏢 Think of JVM like a Restaurant.

| Restaurant | JVM |
|------------|-----|
| 👨‍🍳 Chef | Execution Engine |
| 📖 Menu | Method Area |
| 🍽️ Kitchen | Heap |
| 👨‍🍳 Work Table | Stack |
| 🧹 Cleaner | Garbage Collector |
| 📦 Waiter | Class Loader |

---

# ✅ Advantages

- 🌍 Platform Independent
- ⚡ High Performance using JIT
- 🗑️ Automatic Garbage Collection
- 🔒 Secure
- 💾 Efficient Memory Management

---

# ❌ Disadvantages

- 🚀 Startup Time
- 💾 Higher Memory Usage
- ⚙️ Performance Overhead compared to Native Applications

---

# 🎯 Interview Questions

### ❓ What are the components of JVM?

- 📂 Class Loader
- 💾 Runtime Data Area
- ⚙️ Execution Engine
- 🔗 JNI
- 🖥️ Native Libraries

---

### ❓ Which memory stores Objects?

🟩 Heap Memory

---

### ❓ Which memory stores Local Variables?

🟨 Java Stack

---

### ❓ Which memory is shared among all Threads?

- 🟦 Method Area
- 🟩 Heap Memory

---

### ❓ Difference Between Stack & Heap

| 🟨 Stack | 🟩 Heap |
|-----------|---------|
| Local Variables | Objects |
| Thread Specific | Shared |
| Faster | Slower |
| Auto Cleared | GC Managed |

---

# 💡 Best Practices

✔️ Avoid creating unnecessary objects

✔️ Close Resources properly

✔️ Use Try-With-Resources

✔️ Prevent Memory Leaks

---

# 📝 Summary

> ✅ JVM loads classes, manages memory, executes bytecode, performs garbage collection, and enables Java's **"Write Once, Run Anywhere"** capability.
