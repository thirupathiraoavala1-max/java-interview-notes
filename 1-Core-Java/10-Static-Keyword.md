# ⚡ Static Keyword in Java

> 💡 The **`static`** keyword belongs to the **class** rather than an individual object. It is used to share variables, methods, blocks, and nested classes among all instances of a class.

---

# 🎯 Why Do We Need `static`?

Imagine creating multiple `Employee` objects.

```java
Employee emp1 = new Employee();
Employee emp2 = new Employee();
Employee emp3 = new Employee();
```

All employees work for the same company:

```text
Company = "OpenAI"
```

Instead of storing `"OpenAI"` in every object, we store it **once** using the `static` keyword.

This saves memory and improves efficiency.

---

# 📚 Where Can We Use `static`?

The `static` keyword can be applied to:

- 📦 Static Variables
- ⚙️ Static Methods
- 🧱 Static Blocks
- 🏛️ Static Nested Classes
- 📥 Static Import

---

# 🏗️ Memory Allocation

```text
                 JVM Memory

        ┌──────────────────────┐
        │     Method Area      │
        │----------------------│
        │ static variables     │
        │ static methods       │
        │ static blocks        │
        └──────────────────────┘
                   ▲
                   │
     Shared by all objects
                   │
        ┌──────────────────────┐
        │       Heap           │
        │----------------------│
        │ Object 1             │
        │ Object 2             │
        │ Object 3             │
        └──────────────────────┘
```

---

# 🔹 Static Variable

## 📖 Definition

A static variable belongs to the **class**, not to individual objects.

Only **one copy** exists, regardless of how many objects are created.

---

## 💻 Example

```java
class Employee {

    static String company = "OpenAI";

    String name;

    Employee(String name) {

        this.name = name;

    }

}
```

Usage

```java
Employee emp1 = new Employee("John");
Employee emp2 = new Employee("Alice");

System.out.println(Employee.company);
```

---

# 🌍 Real-World Example

🏢 Company Name

Every employee has a different name.

But the company name is the same for everyone.

Hence,

```java
static String company;
```

---

# 🔹 Static Method

## 📖 Definition

A static method belongs to the class and can be called without creating an object.

---

## 💻 Example

```java
class Calculator {

    static int add(int a, int b) {

        return a + b;

    }

}
```

Usage

```java
int result = Calculator.add(10, 20);

System.out.println(result);
```

---

## 📌 Rules

A static method:

- ✅ Can access static members directly.
- ❌ Cannot access instance variables directly.
- ❌ Cannot use `this` or `super`.

---

# 🔹 Static Block

## 📖 Definition

A static block executes **only once**, when the class is loaded into memory.

It is mainly used for initializing static variables.

---

## 💻 Example

```java
class Employee {

    static {

        System.out.println("Static Block Executed");

    }

}
```

Output

```text
Static Block Executed
```

---

# 🔹 Static Nested Class

A class declared as `static` inside another class.

---

## 💻 Example

```java
class Outer {

    static class Inner {

        void display() {

            System.out.println("Static Nested Class");

        }

    }

}
```

Usage

```java
Outer.Inner obj = new Outer.Inner();

obj.display();
```

---

# 🔹 Static Import

Allows static members to be used without the class name.

---

## 💻 Example

```java
import static java.lang.Math.*;

public class Demo {

    public static void main(String[] args) {

        System.out.println(sqrt(25));

    }

}
```

Output

```text
5.0
```

---

# 📊 Static Variable vs Instance Variable

| Feature | Static Variable | Instance Variable |
|----------|----------------|-------------------|
| Belongs To | Class | Object |
| Memory | Method Area | Heap |
| Copies | One | One per Object |
| Access | Class Name | Object Reference |

---

# ⚖️ Static Method vs Instance Method

| Static Method | Instance Method |
|---------------|-----------------|
| Belongs to Class | Belongs to Object |
| No Object Required | Object Required |
| Cannot access instance members directly | Can access both instance and static members |
| Cannot use `this` | Can use `this` |

---

# 🔄 Execution Order

```text
Program Starts
      │
      ▼
Static Variables
      │
      ▼
Static Block
      │
      ▼
main()
      │
      ▼
Constructor
```

---

# 🌍 Real-World Analogy

Imagine a school.

🏫 School Name → Static Variable

👨‍🎓 Student Name → Instance Variable

The school name is shared by all students, while each student has a unique name.

---

# ❓ Interview Questions

## 1️⃣ What is the `static` keyword?

The `static` keyword makes a member belong to the **class** instead of an object.

---

## 2️⃣ Can a static method access instance variables?

❌ No.

A static method can directly access only static members.

---

## 3️⃣ Can we use `this` inside a static method?

❌ No.

`this` refers to the current object, but static methods belong to the class.

---

## 4️⃣ Why is the `main()` method static?

Because the JVM calls it **before creating any object**.

Declaring it `static` allows the JVM to invoke it directly.

---

## 5️⃣ Can constructors be static?

❌ No.

Constructors initialize objects, whereas `static` belongs to the class.

---

## 6️⃣ How many copies of a static variable exist?

✅ Only **one copy**, shared by all objects.

---

# 💡 Best Practices

✅ Use `static` for constants and utility methods.

✅ Use static variables only for shared data.

✅ Avoid excessive use of static variables to reduce tight coupling.

✅ Keep static blocks simple and lightweight.

---

# 📝 Summary

| Member | Can be Static? |
|----------|:-------------:|
| Variable | ✅ |
| Method | ✅ |
| Block | ✅ |
| Nested Class | ✅ |
| Constructor | ❌ |

---

# 🎯 Key Takeaway

> The **`static` keyword** belongs to the **class**, not to individual objects. It enables memory sharing, utility methods, one-time initialization, and efficient resource management. Understanding `static` is essential for Java interviews and for designing clean, efficient applications.