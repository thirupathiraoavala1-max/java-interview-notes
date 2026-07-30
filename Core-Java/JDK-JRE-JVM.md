# JDK, JRE, and JVM

## Introduction

Java follows the principle:

> **Write Once, Run Anywhere (WORA)**

This is possible because of the Java Virtual Machine (JVM), which allows Java programs to run on different operating systems.

---

## What is JDK?

**JDK (Java Development Kit)** is a software package used to develop Java applications.

It contains everything required to write, compile, and run Java programs.

### JDK Includes

- JRE
- Java Compiler (`javac`)
- Debugger
- Javadoc
- Jar Tool
- Development Utilities

### Use Case

Developers install the JDK to write Java applications.

---

## What is JRE?

**JRE (Java Runtime Environment)** provides the environment required to run Java applications.

It contains:

- JVM
- Core Java Libraries
- Supporting files

### Use Case

End users who only need to run Java applications require the JRE.

---

## What is JVM?

**JVM (Java Virtual Machine)** is an abstract machine responsible for executing Java bytecode.

### Responsibilities

- Loads class files
- Verifies bytecode
- Manages memory
- Performs Garbage Collection
- Executes bytecode

---

## Relationship

```text
JDK
│
├── JRE
│   │
│   ├── JVM
│   └── Java Libraries
│
├── javac
├── javadoc
├── jar
└── Debugger
```

---

## Compilation Flow

```text
Java Source (.java)
        │
        ▼
     javac Compiler
        │
        ▼
Bytecode (.class)
        │
        ▼
       JVM
        │
        ▼
Machine Code
```

---

## Interview Questions

### 1. Difference between JDK, JRE, and JVM?

| JDK | JRE | JVM |
|-----|-----|-----|
| Used for development | Used to run Java programs | Executes bytecode |
| Contains JRE | Contains JVM | Part of JRE |
| Includes compiler | Includes libraries | Performs execution |

---

### 2. Can we run Java code without JDK?

Yes.

If the bytecode (`.class`) is already generated, only the JRE is required to run it.

---

### 3. Can we compile Java code using only JRE?

No.

Compilation requires the `javac` compiler, which is available only in the JDK.

---

## Summary

- **JDK** → Develop Java applications.
- **JRE** → Run Java applications.
- **JVM** → Execute Java bytecode.s