# JVM Architecture

## Introduction

The **Java Virtual Machine (JVM)** is a virtual machine responsible for executing Java bytecode. It acts as an intermediary between Java programs and the operating system, making Java platform-independent.

> **Write Once, Run Anywhere (WORA)** is possible because every operating system has its own JVM implementation.

---

# JVM Architecture

```text
                +----------------------+
                |   Java Source Code   |
                |      (.java)         |
                +----------+-----------+
                           |
                           | javac
                           ▼
                +----------------------+
                |     Bytecode         |
                |      (.class)        |
                +----------+-----------+
                           |
                           ▼
                +----------------------+
                |         JVM          |
                +----------+-----------+
                           |
     +---------------------+----------------------+
     |                     |                      |
     ▼                     ▼                      ▼
 Class Loader       Runtime Data Area     Execution Engine
                                              |
                                              ▼
                                      Native Method Interface
                                              |
                                              ▼
                                         Native Libraries
```

---

# Components of JVM

The JVM consists of the following major components:

1. Class Loader Subsystem
2. Runtime Data Areas
3. Execution Engine
4. Native Method Interface (JNI)
5. Native Libraries

---

# 1. Class Loader Subsystem

The Class Loader is responsible for loading `.class` files into memory.

### Responsibilities

- Loads class files
- Verifies bytecode
- Allocates memory for classes
- Resolves symbolic references

### Types of Class Loaders

### Bootstrap Class Loader

- Loads Java core classes
- Example:
  - java.lang.String
  - java.util.List

---

### Extension (Platform) Class Loader

Loads extension libraries.

Examples:

- JDK modules
- Platform libraries

---

### Application Class Loader

Loads classes from the application's classpath.

Example:

```java
public class Employee {
}
```

Employee.class is loaded by the Application Class Loader.

---

# 2. Runtime Data Areas

Runtime Data Area is the memory area used during program execution.

It contains:

- Method Area
- Heap
- Java Stack
- PC Register
- Native Method Stack

---

## Method Area

Stores:

- Class metadata
- Static variables
- Runtime constant pool
- Method information

Shared among all threads.

---

## Heap Memory

Stores:

- Objects
- Arrays

Example:

```java
Employee emp = new Employee();
```

The Employee object is created in the Heap.

Shared among all threads.

Managed by the Garbage Collector.

---

## Java Stack

Each thread has its own stack.

Stores:

- Local variables
- Method calls
- Partial results

Example:

```java
public void calculate() {
    int a = 10;
}
```

Variable `a` is stored in the Stack.

---

## PC Register

Each thread has its own Program Counter Register.

Stores the address of the currently executing JVM instruction.

---

## Native Method Stack

Stores information related to native methods written in C/C++.

Example:

```java
System.loadLibrary("example");
```

---

# 3. Execution Engine

The Execution Engine executes the bytecode.

It consists of:

- Interpreter
- JIT Compiler
- Garbage Collector

---

## Interpreter

Reads bytecode line by line and executes it.

### Advantage

Starts execution quickly.

### Disadvantage

Slower for frequently executed code.

---

## JIT (Just-In-Time) Compiler

Converts frequently executed bytecode into native machine code.

Advantages:

- Faster execution
- Better performance

Example:

Frequently executed loops are compiled into native code.

---

## Garbage Collector

Automatically removes unused objects from Heap memory.

Example:

```java
Employee emp = new Employee();

emp = null;
```

The object becomes eligible for garbage collection.

---

# 4. Native Method Interface (JNI)

JNI enables Java code to interact with native applications.

Languages supported include:

- C
- C++

Example:

```java
public native void display();
```

---

# 5. Native Libraries

These are platform-specific libraries such as:

- DLL (Windows)
- SO (Linux)

Used through JNI.

---

# JVM Execution Flow

```text
Java Source (.java)
        │
        ▼
Compiler (javac)
        │
        ▼
Bytecode (.class)
        │
        ▼
Class Loader
        │
        ▼
Runtime Data Area
        │
        ▼
Execution Engine
        │
        ▼
Machine Code
```

---

# Real-World Example

Imagine a restaurant:

- **Class Loader** → Waiter brings the order.
- **Method Area** → Menu shared by everyone.
- **Heap** → Kitchen where dishes are prepared.
- **Java Stack** → Each chef's personal workspace.
- **Execution Engine** → Chef preparing the food.
- **Garbage Collector** → Cleaning staff removing unused plates.

---

# Advantages of JVM

- Platform independent
- Automatic memory management
- Garbage Collection
- Security through bytecode verification
- High performance with JIT compilation

---

# Disadvantages

- Higher memory usage than native applications
- JVM startup time
- Performance overhead for small applications

---

# Interview Questions

### 1. What are the components of JVM?

- Class Loader
- Runtime Data Area
- Execution Engine
- JNI
- Native Libraries

---

### 2. Which memory area stores objects?

**Heap Memory**

---

### 3. Which memory area stores local variables?

**Java Stack**

---

### 4. Which memory area is shared among threads?

- Heap
- Method Area

---

### 5. What is the role of the Class Loader?

It loads `.class` files into JVM memory.

---

### 6. What is the purpose of the JIT Compiler?

It converts frequently executed bytecode into native machine code to improve performance.

---

### 7. Difference between Stack and Heap?

| Stack | Heap |
|--------|------|
| Stores local variables | Stores objects |
| Thread-specific | Shared among threads |
| Faster access | Comparatively slower |
| Automatically cleared after method execution | Managed by the Garbage Collector |

---

# Best Practices

- Avoid unnecessary object creation.
- Release resources using try-with-resources.
- Use appropriate object lifecycles.
- Be aware of memory leaks caused by lingering object references.

---

# Summary

- JVM executes Java bytecode.
- Class Loader loads classes into memory.
- Runtime Data Areas manage program memory.
- Execution Engine runs bytecode using the Interpreter and JIT Compiler.
- Garbage Collector automatically reclaims unused Heap memory.
- JNI allows Java to communicate with native code.