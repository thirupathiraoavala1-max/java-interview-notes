# 🔤 String Class in Java

> 💡 **String** is one of the most commonly used classes in Java. It represents a sequence of characters and is **immutable**, meaning once a String object is created, its value cannot be changed.

---

# 🎯 Why Do We Need Strings?

Almost every Java application works with text.

Examples:

- 👤 User Names
- 📧 Email Addresses
- 🔑 Passwords
- 🌐 URLs
- 📄 JSON/XML Data

Java provides the **String** class to efficiently manage textual data.

---

# 📚 What is a String?

A **String** is an object of the `java.lang.String` class.

```java
String language = "Java";
```

Internally,

```java
String language = new String("Java");
```

---

# 🏗️ How String Objects are Created

There are two ways to create String objects.

```text
            String
               │
      ┌────────┴────────┐
      ▼                 ▼
 Literal           new Keyword
```

---

# 🔹 1. String Literal

```java
String s1 = "Java";
```

Stored inside the **String Constant Pool (SCP)**.

---

# 🔹 2. Using new Keyword

```java
String s2 = new String("Java");
```

Creates a new object in Heap Memory.

---

# 🌊 String Constant Pool (SCP)

The JVM maintains a special memory area called the **String Constant Pool**.

It stores only one copy of each unique String literal.

```text
               String Pool

      +-----------------------+
      | "Java"                |
      | "Spring"              |
      | "Kafka"               |
      +-----------------------+

String s1 = "Java";
String s2 = "Java";

Both s1 and s2 point to the same object.
```

---

# 🧠 Memory Diagram

```java
String s1 = "Java";

String s2 = "Java";

String s3 = new String("Java");
```

```text
               String Pool

          +-------------+
          |   "Java"    |
          +-------------+
             ▲      ▲
             │      │
            s1     s2

Heap
+------------------+
|  String("Java")  |
+------------------+
         ▲
         │
        s3
```

---

# 🔒 Why is String Immutable?

Once created,

```java
String s = "Java";

s = "Spring";
```

A **new String object** is created.

The original `"Java"` object remains unchanged.

---

## Benefits of Immutability

- 🔒 Security
- ⚡ Performance
- 🧵 Thread Safety
- 🌊 String Pool Optimization
- 🔑 Safe HashMap Keys

---

# 🔄 String Operations

```java
String s = "Java";

s.concat(" Programming");

System.out.println(s);
```

Output

```text
Java
```

Correct way:

```java
String s = "Java";

s = s.concat(" Programming");

System.out.println(s);
```

Output

```text
Java Programming
```

---

# ⚖️ == vs equals()

```java
String s1 = "Java";

String s2 = "Java";

String s3 = new String("Java");
```

```java
System.out.println(s1 == s2);

System.out.println(s1 == s3);

System.out.println(s1.equals(s3));
```

Output

```text
true
false
true
```

---

# 📊 String vs StringBuilder vs StringBuffer

| Feature | String | StringBuilder | StringBuffer |
|----------|--------|---------------|--------------|
| Mutable | ❌ No | ✅ Yes | ✅ Yes |
| Thread Safe | ✅ Yes (Immutable) | ❌ No | ✅ Yes |
| Performance | Slow (many modifications) | Fast | Slower than StringBuilder |

---

# 💻 StringBuilder Example

```java
StringBuilder sb = new StringBuilder("Java");

sb.append(" Backend");

System.out.println(sb);
```

Output

```text
Java Backend
```

---

# 💻 StringBuffer Example

```java
StringBuffer sb = new StringBuffer("Java");

sb.append(" Backend");

System.out.println(sb);
```

Output

```text
Java Backend
```

---

# 📌 Common String Methods

| Method | Description |
|----------|-------------|
| `length()` | Returns string length |
| `charAt()` | Returns character at index |
| `substring()` | Returns part of string |
| `contains()` | Checks if substring exists |
| `equals()` | Compares content |
| `equalsIgnoreCase()` | Ignores case while comparing |
| `toUpperCase()` | Converts to uppercase |
| `toLowerCase()` | Converts to lowercase |
| `trim()` | Removes leading and trailing spaces |
| `replace()` | Replaces characters |
| `split()` | Splits string into array |
| `startsWith()` | Checks prefix |
| `endsWith()` | Checks suffix |

---

# 🌍 Real-World Analogy

Imagine a printed book.

📖 Once printed,

you cannot change the existing pages.

Instead,

a **new edition** is printed.

Similarly,

Strings are immutable.

---

# 📊 String Memory Flow

```text
String s = "Java"

      │
      ▼
String Constant Pool

      │
      ▼
Immutable Object

      │
      ▼
Modification

      │
      ▼
New Object Created
```

---

# ❓ Interview Questions

## 1️⃣ Why is String immutable?

Because immutable objects are:

- Secure
- Thread-safe
- Cache-friendly
- Efficient in the String Pool

---

## 2️⃣ Where are String literals stored?

✅ String Constant Pool (SCP)

---

## 3️⃣ Difference between String and StringBuilder?

| String | StringBuilder |
|---------|---------------|
| Immutable | Mutable |
| Slower for modifications | Faster |
| Thread-safe by immutability | Not thread-safe |

---

## 4️⃣ Difference between StringBuilder and StringBuffer?

| StringBuilder | StringBuffer |
|---------------|--------------|
| Faster | Slower |
| Not synchronized | Synchronized |
| Not thread-safe | Thread-safe |

---

## 5️⃣ Why is String used as a HashMap key?

Because it is immutable.

Its hash code never changes after creation.

---

## 6️⃣ What is the String Constant Pool?

A special memory area in the JVM that stores one copy of each unique String literal to save memory.

---

# 💡 Best Practices

✅ Use **String** for fixed text.

✅ Use **StringBuilder** for single-threaded string modifications.

✅ Use **StringBuffer** for multi-threaded string modifications.

✅ Prefer `.equals()` instead of `==` when comparing String values.

✅ Avoid unnecessary use of `new String()`.

---

# 📝 Summary

| Concept | Description |
|----------|-------------|
| 🔤 String | Immutable sequence of characters |
| 🌊 String Pool | Stores unique String literals |
| 🔒 Immutable | Cannot be modified after creation |
| ⚡ StringBuilder | Mutable and fast |
| 🧵 StringBuffer | Mutable and thread-safe |

---

# 🎯 Key Takeaway

> The **String** class is one of Java's most fundamental classes. Understanding **immutability**, the **String Constant Pool**, **memory management**, and the differences between **String**, **StringBuilder**, and **StringBuffer** is essential for writing efficient Java applications and succeeding in Java backend interviews.