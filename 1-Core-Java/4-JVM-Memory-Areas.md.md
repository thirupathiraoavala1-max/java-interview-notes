# 💾 JVM Memory Areas

> 💡 **JVM Memory Areas** define how memory is organized during the execution of a Java program. Each memory area has a specific responsibility for storing classes, objects, methods, and thread-related data.

---

# 🏗️ JVM Memory Structure

```text
                      🚀 JVM
                        │
     ┌──────────────────┼──────────────────┐
     │                  │                  │
     ▼                  ▼                  ▼
🟦 Method Area      🟩 Heap          🧵 Thread
                                          │
                              ┌───────────┼────────────┐
                              ▼           ▼            ▼
                         🟨 Stack    🟧 PC Register  🟥 Native Stack
```

---

# 🎯 Why Do We Need JVM Memory Areas?

A Java application creates many objects, executes methods, and loads classes.

To manage these efficiently, the JVM divides memory into dedicated areas.

Each area has a specific purpose.

---

# 📚 JVM Memory Areas

| Memory Area | Shared | Stores |
|-------------|--------|--------|
| 🟦 Method Area | ✅ Yes | Class Metadata, Static Variables |
| 🟩 Heap | ✅ Yes | Objects & Arrays |
| 🟨 Java Stack | ❌ No | Local Variables & Method Calls |
| 🟧 PC Register | ❌ No | Current Instruction Address |
| 🟥 Native Method Stack | ❌ No | Native Method Information |

---

# 🟦 1. Method Area

## 📖 Definition

The **Method Area** stores information that is common to all objects of a class.

### 📦 Stores

- Class Metadata
- Method Information
- Runtime Constant Pool
- Static Variables
- Bytecode of Methods

### ✅ Shared?

Yes, it is shared among all threads.

### 💻 Example

```java
class Employee {

    static String company = "OpenAI";

}
```

The variable `company` is stored in the **Method Area**.

---

# 🟩 2. Heap Memory

## 📖 Definition

The **Heap** is the largest memory area in the JVM.

It stores:

- Objects
- Arrays

Every object created using the `new` keyword is allocated in the Heap.

### 💻 Example

```java
Employee emp = new Employee();
```

The `Employee` object is created in the **Heap**.

### ✅ Shared?

Yes.

### 🗑️ Managed By

Garbage Collector

---

# 🟨 3. Java Stack

## 📖 Definition

Every thread has its own **Java Stack**.

It stores:

- Local Variables
- Method Calls
- Primitive Data
- Partial Results

### 💻 Example

```java
public void display() {

    int age = 25;

}
```

The variable `age` is stored in the **Stack**.

---

## 📚 Stack Frame

Whenever a method is called, a **Stack Frame** is created.

```text
┌───────────────────┐
│ display()         │
├───────────────────┤
│ calculate()       │
├───────────────────┤
│ main()            │
└───────────────────┘
```

When a method finishes, its stack frame is automatically removed.

---

# 🟧 4. Program Counter (PC) Register

## 📖 Definition

Each thread has its own **Program Counter Register**.

It stores:

- Address of the currently executing JVM instruction.

### Example

If a thread is executing line 20 of a method, the PC Register points to that instruction.

---

# 🟥 5. Native Method Stack

## 📖 Definition

Stores information related to native methods written in languages like:

- C
- C++

### Example

```java
System.loadLibrary("example");
```

The execution details of native methods are managed in the Native Method Stack.

---

# 🔄 Memory Allocation Example

```java
class Employee {

    static String company = "OpenAI";

    String name;

    public static void main(String[] args) {

        Employee emp = new Employee();

        emp.name = "John";

    }

}
```

### Memory Layout

```text
🟦 Method Area
-----------------------
Employee.class
company = "OpenAI"

🟩 Heap
-----------------------
Employee Object
name = "John"

🟨 Stack
-----------------------
main()
emp (reference)
```

---

# 🌍 Real-World Analogy

Imagine a company office.

| Office | JVM Memory |
|---------|------------|
| 📚 Company Rule Book | 🟦 Method Area |
| 🏢 Warehouse | 🟩 Heap |
| 👨‍💼 Employee Desk | 🟨 Stack |
| 📍 Current Task Board | 🟧 PC Register |
| 🛠️ External Service Team | 🟥 Native Stack |

---

# ⚖️ Heap vs Stack

| 🟩 Heap | 🟨 Stack |
|----------|----------|
| Stores Objects | Stores Local Variables |
| Shared Memory | Thread Specific |
| Managed by Garbage Collector | Automatically Cleared |
| Larger Memory | Smaller Memory |
| Slower Access | Faster Access |

---

# ❓ Interview Questions

## 1️⃣ Which memory area stores objects?

✅ Heap Memory

---

## 2️⃣ Which memory area stores local variables?

✅ Java Stack

---

## 3️⃣ Which memory area stores static variables?

✅ Method Area

---

## 4️⃣ Which memory area is shared among threads?

- 🟦 Method Area
- 🟩 Heap Memory

---

## 5️⃣ Which memory area is thread-specific?

- 🟨 Java Stack
- 🟧 PC Register
- 🟥 Native Method Stack

---

## 6️⃣ Who manages Heap Memory?

🗑️ Garbage Collector

---

# 💡 Best Practices

✅ Avoid creating unnecessary objects.

✅ Reuse objects whenever possible.

✅ Use local variables efficiently.

✅ Prevent memory leaks by removing unused references.

✅ Close resources using **try-with-resources**.

---

# 📝 Summary

| Memory Area | Purpose |
|-------------|---------|
| 🟦 Method Area | Stores Class Information |
| 🟩 Heap | Stores Objects |
| 🟨 Stack | Stores Local Variables |
| 🟧 PC Register | Stores Current Instruction |
| 🟥 Native Stack | Stores Native Method Data |

---

# 🎯 Key Takeaway

> JVM memory is divided into **five main areas**, each serving a unique purpose:
>
> - 🟦 **Method Area** → Class metadata and static data
> - 🟩 **Heap** → Objects and arrays
> - 🟨 **Stack** → Local variables and method execution
> - 🟧 **PC Register** → Current instruction address
> - 🟥 **Native Method Stack** → Native method execution
>
> Understanding these memory areas is essential for writing efficient Java applications and answering Java interview questions with confidence.