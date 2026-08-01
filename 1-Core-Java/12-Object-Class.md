# 🌍 Object Class in Java

> 💡 The **Object** class is the **root class** of the Java class hierarchy. Every class in Java directly or indirectly extends the `Object` class and inherits its common methods.

---

# 🎯 Why Do We Need the Object Class?

Imagine you have different classes.

```java
class Employee {}

class Student {}

class Product {}
```

Although these classes are unrelated, they all inherit common behaviors like:

- Comparing objects
- Printing object information
- Getting runtime class details
- Cloning objects
- Thread communication

These common functionalities are provided by the **Object** class.

---

# 📚 Object Class Hierarchy

```text
                Object
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
    Employee   Student   Product
```

Every class in Java automatically extends `Object`.

---

# 📦 Common Methods of Object Class

```text
                 Object
                    │
     ┌──────────────┼──────────────┐
     ▼              ▼              ▼
 equals()      hashCode()      toString()
     │              │              │
 clone()      getClass()      finalize()*
     │
 wait()
 notify()
 notifyAll()
```

> ⚠️ `finalize()` is **deprecated** and should not be used in modern Java.

---

# 🔹 1. toString()

## 📖 Definition

Returns the string representation of an object.

### 💻 Example

```java
class Employee {

    String name = "John";

}

public class Demo {

    public static void main(String[] args) {

        Employee emp = new Employee();

        System.out.println(emp);

    }

}
```

### Output

```text
Employee@5acf9800
```

---

## ✅ Overriding toString()

```java
class Employee {

    String name = "John";

    @Override
    public String toString() {

        return "Employee{name='" + name + "'}";

    }

}
```

### Output

```text
Employee{name='John'}
```

---

# 🔹 2. equals()

## 📖 Definition

Used to compare the **contents (logical equality)** of two objects.

---

### 💻 Example

```java
String s1 = new String("Java");

String s2 = new String("Java");

System.out.println(s1.equals(s2));
```

### Output

```text
true
```

---

# 🔹 3. hashCode()

## 📖 Definition

Returns an integer hash value for an object.

Used extensively in:

- HashMap
- HashSet
- Hashtable

---

### 💻 Example

```java
String s = "Java";

System.out.println(s.hashCode());
```

---

# 🔹 4. getClass()

Returns the runtime class of an object.

### Example

```java
Employee emp = new Employee();

System.out.println(emp.getClass());
```

### Output

```text
class Employee
```

---

# 🔹 5. clone()

Creates a copy of an object.

### Example

```java
class Employee implements Cloneable {

    int id = 101;

    @Override
    protected Object clone() throws CloneNotSupportedException {

        return super.clone();

    }

}
```

---

# 🔹 6. wait()

Causes the current thread to wait until another thread notifies it.

Used in **Multithreading**.

---

# 🔹 7. notify()

Wakes up one waiting thread.

---

# 🔹 8. notifyAll()

Wakes up all waiting threads.

---

# 🔹 9. finalize() *(Deprecated)*

Called by the Garbage Collector before removing an object.

⚠️ Deprecated since Java 9 and removed from modern Java usage.

Use **try-with-resources** or **AutoCloseable** instead.

---

# ⚖️ == vs equals()

| `==` | `equals()` |
|-------|------------|
| Compares references | Compares object content |
| Checks memory address | Checks logical equality |
| Cannot be overridden | Can be overridden |

---

## 💻 Example

```java
String s1 = new String("Java");

String s2 = new String("Java");

System.out.println(s1 == s2);

System.out.println(s1.equals(s2));
```

### Output

```text
false
true
```

---

# ⚖️ hashCode() vs equals()

| equals() | hashCode() |
|-----------|------------|
| Compares content | Generates hash value |
| Returns boolean | Returns integer |
| Used for logical equality | Used for bucket selection in hash-based collections |

---

# 🔄 equals() and hashCode() Contract

If two objects are equal according to `equals()`:

```java
obj1.equals(obj2) == true
```

Then:

```java
obj1.hashCode() == obj2.hashCode()
```

This contract is essential for collections like `HashMap` and `HashSet`.

---

# 🌍 Real-World Analogy

Imagine an Aadhaar Card.

👤 Person → Object

🆔 Aadhaar Number → hashCode()

📄 Personal Details → equals()

Two people with identical details are logically equal, while the Aadhaar number helps uniquely organize records.

---

# 💻 Complete Example

```java
class Employee {

    int id;

    Employee(int id) {

        this.id = id;

    }

    @Override
    public boolean equals(Object obj) {

        if (this == obj)
            return true;

        if (!(obj instanceof Employee))
            return false;

        Employee emp = (Employee) obj;

        return this.id == emp.id;

    }

    @Override
    public int hashCode() {

        return Integer.hashCode(id);

    }

    @Override
    public String toString() {

        return "Employee{id=" + id + "}";

    }

}
```

---

# ❓ Interview Questions

## 1️⃣ What is the Object class?

The root class of the Java class hierarchy.

---

## 2️⃣ Which class does every Java class extend?

✅ `java.lang.Object`

---

## 3️⃣ What is the difference between `==` and `equals()`?

- `==` compares references.
- `equals()` compares object content.

---

## 4️⃣ Why should `equals()` and `hashCode()` be overridden together?

To maintain the contract required by hash-based collections like `HashMap` and `HashSet`.

---

## 5️⃣ What is the purpose of `toString()`?

It provides a readable string representation of an object.

---

## 6️⃣ What is `getClass()` used for?

To get the runtime class information of an object.

---

## 7️⃣ Why is `finalize()` deprecated?

Because it is unpredictable, inefficient, and modern Java provides better resource management techniques like **try-with-resources**.

---

# 💡 Best Practices

✅ Always override `hashCode()` when overriding `equals()`.

✅ Override `toString()` for better logging and debugging.

✅ Avoid using `finalize()`.

✅ Use `clone()` only when necessary; prefer copy constructors or factory methods for object copying.

---

# 📝 Summary

| Method | Purpose |
|---------|----------|
| `toString()` | Returns string representation |
| `equals()` | Compares object content |
| `hashCode()` | Generates hash value |
| `getClass()` | Returns runtime class |
| `clone()` | Creates object copy |
| `wait()` | Pauses current thread |
| `notify()` | Wakes one waiting thread |
| `notifyAll()` | Wakes all waiting threads |
| `finalize()` | Deprecated cleanup method |

---

# 🎯 Key Takeaway

> The **Object** class is the foundation of Java's object-oriented model. Understanding methods like **`equals()`**, **`hashCode()`**, **`toString()`**, and **`getClass()`** is essential for writing robust Java applications and succeeding in Java backend interviews.