# 🗺️ HashMap Basics in Java

> 💡 **HashMap** is one of the most important data structures in Java. It stores data as **Key-Value pairs** and provides **very fast** insertion, deletion, and searching using a technique called **Hashing**.

---

# 🎯 Learning Objectives

After completing this chapter, you will understand:

- ✅ What is HashMap?
- ✅ Why HashMap is needed?
- ✅ Features of HashMap
- ✅ Internal Architecture (Overview)
- ✅ Key-Value Pair
- ✅ CRUD Operations
- ✅ Iterating HashMap
- ✅ Null Keys & Values
- ✅ Time Complexity
- ✅ Real-world Examples
- ✅ Interview Questions

---

# 🤔 Why Do We Need HashMap?

Imagine you are developing an **Employee Management System**.

Without HashMap, employee records might be stored in a list.

```text
Employee List

101 → John
102 → Alice
103 → David
104 → Bob
```

Suppose you want to find Employee **103**.

You must search one by one.

```text
101 ❌

102 ❌

103 ✅
```

Time Complexity

```
O(n)
```

As the number of employees grows, searching becomes slower.

---

## 🚀 Using HashMap

```text
Key        Value

101  →  John

102  →  Alice

103  →  David

104  →  Bob
```

Now searching works like this:

```text
Employee ID

↓

Hash Function

↓

Bucket

↓

Employee Found
```

Average Time Complexity

```
O(1)
```

This is why HashMap is one of the fastest collections in Java.

---

# 📚 What is HashMap?

HashMap is a class in the Java Collections Framework that stores data as **Key-Value pairs**.

Each key must be **unique**, while values may be duplicated.

```java
Map<Integer, String> employees = new HashMap<>();

employees.put(101, "John");
employees.put(102, "Alice");
employees.put(103, "David");
```

Output

```text
101 → John

102 → Alice

103 → David
```

---

# 🔑 Understanding Key-Value Pair

Every record in a HashMap consists of two parts.

```text
+---------+----------------+
|   Key   |     Value      |
+---------+----------------+
| 101     | John           |
| 102     | Alice          |
| 103     | David          |
+---------+----------------+
```

Think of it like a dictionary.

```text
Word

↓

Meaning
```

or

```text
Student ID

↓

Student Details
```

---

# 🏗 Class Hierarchy

```text
               Object
                  │
                  ▼
          AbstractMap
                  │
                  ▼
              HashMap
```

HashMap implements the **Map** interface.

> 📌 **Note:** `Map` is **not** a child of the `Collection` interface.

---

# ✨ Features of HashMap

✅ Stores data in **Key → Value** format.

✅ Keys must be unique.

✅ Duplicate values are allowed.

✅ Allows one null key.

✅ Allows multiple null values.

✅ Average search time is **O(1)**.

✅ Not synchronized.

✅ Does not maintain insertion order.

---

# 🧠 Internal Architecture (Overview)

Internally HashMap uses a **Hash Table**.

```text
                HashMap
                    │
                    ▼
             Hash Table
                    │
                    ▼
        +----+----+----+----+
Index   | 0  | 1  | 2  | 3  |
        +----+----+----+----+
                    │
                    ▼
              Key-Value Pair
```

Each location in the hash table is called a **Bucket**.

> 💡 We will explore buckets and hashing in detail in the next chapter.

---

# 💻 Creating a HashMap

```java
Map<Integer, String> map = new HashMap<>();
```

---

# 📥 Adding Elements

Use `put()` to insert key-value pairs.

```java
map.put(101, "John");
map.put(102, "Alice");
map.put(103, "David");

System.out.println(map);
```

Output

```text
{101=John, 102=Alice, 103=David}
```

---

# 📖 Reading Elements

Use `get()` to retrieve a value.

```java
System.out.println(map.get(102));
```

Output

```text
Alice
```

---

# ✏️ Updating Elements

If the key already exists, `put()` updates its value.

```java
map.put(102, "Bob");

System.out.println(map);
```

Output

```text
{101=John, 102=Bob, 103=David}
```

---

# ❌ Removing Elements

```java
map.remove(101);

System.out.println(map);
```

Output

```text
{102=Bob, 103=David}
```

---

# 🔍 Searching

### containsKey()

```java
System.out.println(map.containsKey(103));
```

Output

```text
true
```

---

### containsValue()

```java
System.out.println(map.containsValue("David"));
```

Output

```text
true
```

---

# 🔄 Replacing a Value

```java
map.replace(103, "Charlie");

System.out.println(map);
```

Output

```text
{102=Bob, 103=Charlie}
```

---

# 🗑 Clearing the Map

```java
map.clear();
```

---

# 📏 Checking Size

```java
System.out.println(map.size());
```

---

# ❓ Checking Empty

```java
System.out.println(map.isEmpty());
```

---

# 🔄 Iterating a HashMap

## 1️⃣ Using keySet()

```java
for(Integer key : map.keySet()){

    System.out.println(key);

}
```

---

## 2️⃣ Using values()

```java
for(String value : map.values()){

    System.out.println(value);

}
```

---

## 3️⃣ Using entrySet() ⭐ Recommended

```java
for(Map.Entry<Integer, String> entry : map.entrySet()){

    System.out.println(entry.getKey() + " : " + entry.getValue());

}
```

---

## 4️⃣ Using forEach()

```java
map.forEach((key, value) ->
        System.out.println(key + " -> " + value));
```

---

# 🚫 Null Keys and Null Values

HashMap allows:

- ✅ One null key
- ✅ Multiple null values

Example

```java
map.put(null, "Admin");
map.put(101, null);
map.put(102, null);
```

Output

```text
{null=Admin, 101=null, 102=null}
```

---

# 🔁 Duplicate Keys

Duplicate keys are **not allowed**.

If the same key is inserted again, the value is replaced.

```java
map.put(101, "John");
map.put(101, "Alice");
```

Output

```text
{101=Alice}
```

---

# 📊 Time Complexity

| Operation | Average | Worst |
|-----------|---------|--------|
| put() | O(1) | O(n) |
| get() | O(1) | O(n) |
| remove() | O(1) | O(n) |
| containsKey() | O(1) | O(n) |
| containsValue() | O(n) | O(n) |

> 💡 In Java 8, heavily-collided buckets can become Red-Black Trees, improving worst-case lookups to **O(log n)**.

---

# 🌍 Real-World Examples

HashMap is used in:

- 👤 Employee Management
- 🛒 E-Commerce Product Catalog
- 📧 Email Lookup
- 🏦 Banking Systems
- 📱 Contact List
- 🌐 DNS Cache
- 🔑 Authentication & Sessions
- ⚙ Configuration Properties

---

# 💡 Best Practices

✅ Use immutable objects as keys whenever possible.

✅ Override `equals()` and `hashCode()` for custom key classes.

✅ Use `entrySet()` for efficient iteration.

✅ Specify an initial capacity if you know the expected number of entries.

---

# ⚠️ Common Mistakes

❌ Assuming HashMap maintains insertion order.

❌ Forgetting to override `hashCode()` when overriding `equals()`.

❌ Using mutable objects as keys.

❌ Using `containsValue()` for frequent lookups (it's O(n)).

---

# 🎯 Interview Notes

📌 HashMap stores data as **Key → Value** pairs.

📌 Keys must be unique.

📌 Duplicate values are allowed.

📌 One null key is allowed.

📌 Multiple null values are allowed.

📌 Average lookup is **O(1)**.

📌 HashMap is **not thread-safe**.

📌 HashMap does **not guarantee iteration order**.

---

# ❓ Interview Questions

### 1. What is HashMap?

A HashMap is a key-value data structure that uses hashing for fast storage and retrieval.

---

### 2. Does HashMap allow duplicate keys?

❌ No.

---

### 3. Does HashMap allow duplicate values?

✅ Yes.

---

### 4. Does HashMap allow null?

✅ One null key and multiple null values.

---

### 5. Is HashMap synchronized?

❌ No.

---

### 6. What is the average time complexity of `get()`?

✅ O(1)

---

### 7. Which iteration method is preferred?

✅ `entrySet()` because it avoids an extra lookup.

---

### 8. Does HashMap maintain insertion order?

❌ No.

Use `LinkedHashMap` if insertion order is required.

---

### 9. Can HashMap store custom objects as keys?

✅ Yes, but you should properly override `equals()` and `hashCode()`.

---

### 10. What is the internal data structure of HashMap?

A **Hash Table** consisting of an array of buckets.

---

# 📝 Summary

| Feature | HashMap |
|----------|---------|
| Stores | Key → Value |
| Duplicate Keys | ❌ No |
| Duplicate Values | ✅ Yes |
| Null Key | ✅ One |
| Null Values | ✅ Multiple |
| Ordered | ❌ No |
| Thread Safe | ❌ No |
| Average Complexity | ⭐ O(1) |
| Internal Structure | Hash Table |

---

# 🎯 Key Takeaway

> **HashMap** is the most commonly used implementation of the `Map` interface in Java. It provides **fast insertion, retrieval, and deletion** using **hashing**, making it ideal for storing and accessing data through unique keys. Understanding its basic operations and characteristics is the foundation for mastering its internal workings, which we will explore in the next chapters.